# 📦 JS Bagian 3: Gudang Data (Data Structures)

> **Status:** Jantung Aplikasi
> **Prinsip:** Array itu "Rak", Object itu "Kotak Barang". Jangan simpan barang tanpa kotak di lantai!

---

## 📚 1. Array (Daftar/List)
Kumpulan data yang berurutan. Selalu menggunakan **Kurung Siku `[]`**.

### 📐 Rumus / Syntax
```javascript
const namaList = [data1, data2, data3];
```

### 🛠️ Jurus Sakti Array:

#### A. `.push()` (Menambah Data) ➕
Memasukkan data baru ke **urutan paling belakang**.
* **Rumus:** `namaArray.push(dataBaru);`
* **Contoh:**
  ```javascript
  const daftarJajan = ["Cilok", "Batagor"];
  daftarJajan.push("Seblak"); 
  // Hasil: ["Cilok", "Batagor", "Seblak"]
  ```

#### B. `.filter()` (Menyaring Data) 🔍
Mencari data yang cocok dan membuang yang tidak cocok (Menghasilkan Array Baru).

* **Rumus:**
  ```javascript
  const hasilSaring = arrayLama.filter((item) => {
    return kondisi_harus_true_biar_lolos;
  });
  ```
* **Contoh (Cari Pengeluaran Besar):**
  ```javascript
  const pengeluaran = [10000, 5000, 50000, 2000];
  
  // Ambil yang di atas 20rb saja
  const boros = pengeluaran.filter((uang) => {
    return uang > 20000;
  });
  
  console.log(boros); // Output: [50000]
  ```

---

## 🗃️ 2. Object (Detail Barang)
Satu kesatuan data yang punya label (Key & Value). Selalu menggunakan **Kurung Kurawal `{}`**.

### 📐 Rumus / Syntax
```javascript
const namaObject = {
  kunci: "nilai",
  kunci2: 123
};
```

### 📝 Cara Akses Data:
* **Dot Notation (Titik):** `object.kunci` (Paling sering dipakai).
* **Bracket Notation (Kurung):** `object["kunci"]` (Dipakai kalau nama kuncinya aneh/dinamis).

### 🧪 Contoh (Satu Transaksi Dompet):
```javascript
const transaksi = {
  id: 1,
  nama: "Beli Kuota",
  harga: 50000,
  kategori: "Internet"
};

console.log(transaksi.nama);  // Output: "Beli Kuota"
console.log(transaksi.harga); // Output: 50000
```

### 💡 Kombinasi Maut: Array of Objects
Ini bentuk data standar aplikasi dunia nyata (termasuk "Dompet"-mu nanti).
```javascript
const riwayatBelanja = [
  { id: 1, nama: "Es Teh", harga: 3000 },
  { id: 2, nama: "Nasi Pecel", harga: 12000 }
];

// Cara ambil harga Nasi Pecel (Item ke-2, index 1)
console.log(riwayatBelanja[1].harga); // 12000
```

---

## 🔌 3. JSON (Jembatan Komunikasi)
Format teks standar agar data JS bisa disimpan atau dikirim.

### A. `JSON.stringify()` (Packing / Membungkus) 📦
Mengubah data JS (Array/Object) menjadi **STRING (Teks)** biar bisa disimpan ke LocalStorage/Server.
* **Rumus:** `JSON.stringify(dataAsli)`
* **Contoh:**
  ```javascript
  const data = { user: "Maba", saldo: 0 };
  const dataSiapSimpan = JSON.stringify(data);
  
  console.log(dataSiapSimpan); 
  // Output: '{"user":"Maba","saldo":0}' (Bentuknya teks!)
  ```

### B. `JSON.parse()` (Unpacking / Membuka) 🎁
Mengubah Teks JSON kembali menjadi **Data JS** biar bisa diolah kodingan.
* **Rumus:** `JSON.parse(dataTeks)`
* **Contoh:**
  ```javascript
  const dataDariServer = '{"user":"Maba","saldo":0}';
  const dataAsli = JSON.parse(dataDariServer);
  
  console.log(dataAsli.user); // Output: "Maba"
  ```

---

### 🧪 Studi Kasus: Simpan & Baca di "Dompet"

**1. Saat User Klik "Simpan" (Packing):**
```javascript
// Data Array Transaksi
const listTransaksi = [
  { nama: "Cilok", harga: 5000 },
  { nama: "Kopi", harga: 3000 }
];

// Ubah jadi Teks JSON
const teksJSON = JSON.stringify(listTransaksi);

// Masukkan ke Gudang Browser (LocalStorage)
localStorage.setItem('dompet_data', teksJSON);
```

**2. Saat Halaman Dibuka (Unpacking):**
```javascript
// Ambil teks dari Gudang
const ambilTeks = localStorage.getItem('dompet_data');

// Ubah balik jadi Array biar bisa di-looping
const dataSiapPakai = JSON.parse(ambilTeks);

// Tampilkan ke layar pakai .map() atau .forEach()...
```