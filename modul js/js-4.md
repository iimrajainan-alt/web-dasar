# 🚚 JS Bagian 4: Ingatan & Kurir (Storage & Async)

> **Status:** Fitur Canggih
> **Prinsip:** LocalStorage itu "Memori Jangka Panjang". Fetch itu "Ojol" pengantar data.

---

## 💾 1. LocalStorage (Ingatan Browser)
Tempat menyimpan data di browser user. Data **TIDAK HILANG** walau halaman di-refresh atau browser ditutup.
* **Kapasitas:** Sekitar 5MB (Cukup buat teks JSON banyak).
* **Syarat:** Hanya bisa menyimpan **STRING (Teks)**.

### A. `setItem` (Menyimpan Data) 📥
#### 📐 Rumus / Syntax
```javascript
localStorage.setItem('nama_kunci', 'data_string');
```
* **`nama_kunci`**: Label buat datanya (misal: "username", "saldo").
* **`data_string`**: Isinya (wajib teks). Kalau mau simpan Array/Object, bungkus dulu pakai `JSON.stringify()`.

#### 🧪 Contoh:
```javascript
// Simpan nama user
localStorage.setItem('user_name', 'Maba Ganteng');

// Simpan saldo (Ubah angka jadi string dulu otomatis, tapi lebih aman JSON)
localStorage.setItem('saldo_terakhir', '50000');
```

### B. `getItem` (Mengambil Data) 📤
#### 📐 Rumus / Syntax
```javascript
const variabel = localStorage.getItem('nama_kunci');
```
* **Return:** Mengembalikan `null` jika kuncinya gak ketemu.

#### 🧪 Contoh:
```javascript
const nama = localStorage.getItem('user_name');

if (nama) {
  console.log(`Selamat datang kembali, ${nama}!`);
} else {
  console.log("Kamu siapa? Daftar dulu sana!");
}
```

### C. `removeItem` & `clear` (Menghapus) 🗑️
* `localStorage.removeItem('kunci')`: Hapus satu data spesifik.
* `localStorage.clear()`: Hapus SEMUA data di domain ini (Reset Pabrik).

---

## 🌐 2. Fetch API & Async/Await (Kurir Data)
Cara mengambil data dari server lain (misal: Cek Kurs Rupiah, Cuaca, atau Daftar Film).

### A. Konsep `async` & `await` ⏳
JS itu aslinya **Gak Sabaran**. Kalau disuruh ambil data di internet (yang butuh waktu 2 detik), dia bakal lanjut ke baris bawahnya padahal datanya belum sampai. Hasilnya? Error!
* **Solusi:** Pakai `await` (Tungguin dulu bos!).
* **Syarat:** `await` hanya boleh dipakai di dalam fungsi yang dikasih label `async`.

### B. `fetch()` (Panggil Kurir) 🛵
#### 📐 Rumus Dasar
```javascript
const ambilData = async () => {
  // 1. Panggil kurir ke URL tujuan (Tungguin kurirnya balik bawa paket)
  const response = await fetch('[https://url-api-tujuan.com](https://url-api-tujuan.com)');
  
  // 2. Buka paketnya, baca isinya sebagai JSON (Tungguin proses bukanya)
  const data = await response.json();
  
  // 3. Data siap dipakai
  return data;
};
```

#### 🧪 Contoh Kasus: Cek Kurs Dollar di "Dompet"
Anggap kita mau tahu 1 USD berapa Rupiah hari ini.

```javascript
// 1. Bikin Fungsi ASYNC
const cekKursDollar = async () => {
  try {
    // Request ke API (Pura-pura ada API kurs gratis)
    const respon = await fetch('[https://api.exchangerate-api.com/v4/latest/USD](https://api.exchangerate-api.com/v4/latest/USD)');
    
    // Ubah hasil jadi JSON
    const hasil = await respon.json();
    
    // Ambil data spesifik (misal: rates.IDR)
    const kursRupiah = hasil.rates.IDR;
    
    console.log(`Hari ini 1 Dollar = Rp ${kursRupiah}`);
    
    // Update tampilan HTML (DOM Manipulation dari Bagian 2!)
    document.getElementById('info-kurs').innerText = `Kurs: Rp ${kursRupiah}`;
    
  } catch (error) {
    // Kalau internet mati atau link error, lari ke sini
    console.log("Gagal ambil data bos! Cek kuota.");
  }
};

// Panggil fungsinya
cekKursDollar();
```
# ⏳ Async Function Klasik (Function Declaration)

> **Status:** Gaya Senior (Old School Cool)
> **Kelebihan Utama:** Punya fitur **HOISTING**. Kamu bisa panggil fungsinya di baris 1, padahal fungsinya baru ditulis di baris 100.

---

## 📐 1. Rumus Dasar (Syntax)

```javascript
async function namaFungsi(parameter) {
  // 1. Kode di sini jalan asinkron
  // 2. Bisa pakai keyword 'await' buat nunggu
  const hasil = await prosesLama();
  return hasil;
}
```

### 📝 Aturan Main:
1.  Kata kunci **`async`** wajib ditaruh di **DEPAN** kata `function`.
2.  Kata kunci **`await`** hanya boleh dipakai di **DALAM** kurung kurawal `{}` fungsi ini.
3.  Fungsi ini otomatis mengembalikan **Promise**. Jadi kalau mau ambil hasil `return`-nya di luar, harus di-`then` atau di-`await` lagi.

---

## 🛠️ 2. Penjelasan Detail
Kenapa pakai gaya ini?

* **Hoisting:** Ini beda paling telak sama Arrow Function (`const`). Fungsi ini "diangkat" ke atas oleh JavaScript sebelum kode dijalankan. Jadi aman mau ditaruh di paling bawah file sekalipun.
* **Lebih Terbaca (Opinion):** Buat sebagian orang, tulisan `function` lebih jelas daripada tanda panah `=>`.

---

## 🧪 3. Contoh Penerapan

### Kasus: Mengambil Data Kurs (Hoisting Demo)

Lihat! Kita panggil dulu fungsinya di atas (`cekKurs()`), padahal fungsinya baru dibuat di bawah. Kalau pakai Arrow Function, ini bakal ERROR.

```javascript
// ✅ PANGGIL DULUAN (HOISTING)
cekKurs(); 

// ... baris kode lain ...

// BARU DEKLARASI DI BAWAH
async function cekKurs() {
  try {
    console.log("Sedang menghubungi bank...");
    
    // Pura-pura nunggu 2 detik (Simulasi fetch)
    const respon = await fetch('[https://api.exchangerate-api.com/v4/latest/USD](https://api.exchangerate-api.com/v4/latest/USD)');
    const data = await respon.json();
    
    console.log(`Kurs hari ini: Rp ${data.rates.IDR}`);
    
  } catch (masalah) {
    console.log("Gagal ambil kurs:", masalah);
  }
}
```
---

### ⚔️ Ringkasan Alur Kerja "Dompet Pintar":

1.  **User Input:** Pakai `input` form (Bagian HTML).
2.  **Proses:** Pakai `function` & logic `if/else` (Bagian 1 JS).
3.  **Tampil:** Pakai `document.querySelector` ubah teks (Bagian 2 JS).
4.  **Simpan:** Pakai `localStorage.setItem` biar awet (Bagian 4 JS).
5.  **Bonus:** Pakai `fetch` buat fitur kurs mata uang (Bagian 4 JS).