# 🧠 JS Bagian 1: Otak & Logika (Fundamentals)

> **Status:** Materi Wajib
> **Peringatan Tante:** Ini adalah fondasi. Kalau bagian ini rapuh, aplikasimu bakal *buggy* seumur hidup.

---

## 📦 1. Variabel (Wadah Penyimpan)
Tempat menyimpan data agar bisa dipakai berulang kali.

### 📐 Rumus / Syntax
```javascript
keyword namaVariabel = nilai;
```

### 📝 Penjelasan & Aturan:
1.  **`let`**: Gunakan jika nilai wadah **AKAN BERUBAH** di masa depan (misal: saldo, skor, counter).
2.  **`const`**: Gunakan jika nilai wadah **TETAP/ABADI**. (misal: ID User, Rumus Matematika).
3.  **`var`**: **DILARANG KERAS!** (Jadul, rawan bocor).

### 🧪 Contoh Penerapan:
```javascript
// ✅ CONST: Nama aplikasi gak mungkin ganti-ganti kan?
const namaAplikasi = "Dompet Maba";

// ✅ LET: Saldo pasti naik turun.
let saldo = 50000;

// Re-assign (Mengubah nilai let)
saldo = 40000; // Sah! (Habis beli bakso)

// ❌ Error jika maksa ubah const:
// namaAplikasi = "Dompet Sultan"; // Error!
```

---

## 🔡 2. Tipe Data (Jenis Isi Wadah)
JavaScript perlu tahu jenis data apa yang kamu simpan.

### 📐 Rumus / Syntax
Langsung masukkan nilainya.

### 📝 Penjelasan:
1.  **String**: Teks/Huruf. Wajib diapit kutip (`"` atau `'`) atau backtick (`` ` ``).
2.  **Number**: Angka. Bisa bulat (`100`) atau koma (`10.5`). Bisa dijumlahkan.
3.  **Boolean**: Saklar Logika. Cuma ada `true` (Benar) atau `false` (Salah).

### 🧪 Contoh Penerapan:
```javascript
// String (Teks)
const kategori = "Makanan";

// Number (Angka)
const harga = 15000;

// Boolean (Logika)
const isLapar = true; 
const isKaya = false;
```

---

## ⚙️ 3. Fungsi (Mesin Pemroses)
Membungkus kumpulan perintah agar bisa dipanggil berkali-kali.

### A. Cara Jadul (`function`) 👴
Masih sering ketemu di tutorial lama.
#### 📐 Rumus:
```javascript
function namaFungsi(parameter) {
  return hasil;
}
```

### B. Cara Modern (Arrow Function) 🚀
Lebih ringkas, wajib dikuasai untuk React/Framework modern.
#### 📐 Rumus:
```javascript
const namaFungsi = (parameter) => {
  return hasil;
};
```

### 🧪 Contoh Penerapan (Hitung Pengeluaran):
```javascript
// Cara Modern
const tambahPengeluaran = (saldoAwal, hargaBarang) => {
  const sisa = saldoAwal - hargaBarang;
  return sisa;
};

// Cara Pakai:
let saldoSekarang = tambahPengeluaran(50000, 15000);
console.log(saldoSekarang); // Output: 35000
```

---

## 🚦 4. Pengkondisian (Logika Percabangan)
Membuat program bisa "Berpikir" dan memilih jalan.

### A. IF - ELSE (Logika Standar)
#### 📐 Rumus:
```javascript
if (syarat) {
  // Jalan jika syarat TRUE
} else {
  // Jalan jika syarat FALSE
}
```
#### 🧪 Contoh:
```javascript
let uang = 2000;
if (uang > 5000) {
  console.log("Beli Nasgor");
} else {
  console.log("Beli Promag"); // Jalan ini karena uang cuma 2000
}
```

### B. SWITCH (Logika Banyak Pintu)
Gunakan ini jika pilihannya ada BANYAK tapi syaratnya sederhana (cek nilai pas).
#### 📐 Rumus:
```javascript
switch (kunci) {
  case "nilai1":
    // Aksi 1
    break; // Wajib break biar gak bablas!
  case "nilai2":
    // Aksi 2
    break;
  default:
    // Aksi jika tidak ada yang cocok
}
```
#### 🧪 Contoh:
```javascript
const menu = "Nasi";

switch (menu) {
  case "Nasi":
    console.log("Harga 3000");
    break;
  case "Ayam":
    console.log("Harga 7000");
    break;
  default:
    console.log("Menu gak ada bang");
}
```

---

## 🔄 5. Perulangan (Loops)
Menyuruh komputer melakukan hal yang sama berulang kali.

### A. FOR Loop (Manual & Klasik) ⚙️
Kamu atur sendiri mulai dari mana sampai mana.
#### 📐 Rumus:
```javascript
for (mulai; sampai_kapan; langkah) {
  // Aksi
}
```
#### 🧪 Contoh:
```javascript
// Mulai dari 1; Selama i <= 5; Tambah 1 terus
for (let i = 1; i <= 5; i++) {
  console.log(`Transaksi ke-${i}`);
}
```

### B. MAP (Modern & Otomatis) 🗺️
Khusus Array. Mengubah semua data di dalam daftar.
#### 📐 Rumus:
```javascript
const arrayBaru = arrayLama.map((item) => {
  return item_diubah;
});
```
#### 🧪 Contoh (Diskon Toko):
```javascript
const hargaAsli = [10000, 20000];

// Semua harga didiskon 50%
const hargaDiskon = hargaAsli.map((uang) => {
  return uang * 0.5;
});

console.log(hargaDiskon); // Output: [5000, 10000]
```