# 🏗️ JS Bagian 2: Manipulasi DOM (Tukang Suruh-Suruh)

> **Status:** Jembatan Dunia Nyata
> **Prinsip:** Logic JS (Otak) -> DOM -> HTML/CSS (Wajah). JS menyuruh browser mengubah tampilan.

---

## 🔍 1. Seleksi Elemen (Mencari Target)
Sebelum menyuruh, kamu harus "menunjuk" dulu siapa yang mau disuruh.

### A. `document.getElementById()` (Cara Spesifik) 🎯
Khusus mencari elemen yang punya ID unik. Cepat, tapi kaku.

#### 📐 Rumus / Syntax
```javascript
const variabel = document.getElementById('nama_id_tanpa_pagar');
```

#### 🧪 Contoh:
HTML: `<h1 id="judul">Dompet</h1>`
```javascript
const elemenJudul = document.getElementById('judul');
// Sekarang variabel 'elemenJudul' memegang kendali atas <h1> itu.
```

### B. `document.querySelector()` (Anak Emas / Serba Bisa) 🌟
Bisa mencari ID, Class, atau Tag. Mirip cara CSS memanggil elemen. **Gunakan ini sebagai default!**

#### 📐 Rumus / Syntax
```javascript
// Pakai titik (.) buat class, pagar (#) buat ID
const variabel = document.querySelector('selector_css');
```

#### 🧪 Contoh:
HTML: `<div class="kotak-saldo">...</div>`
```javascript
// Mencari elemen dengan class "kotak-saldo"
const kotak = document.querySelector('.kotak-saldo');

// Mencari tombol di dalam form (Spesifik)
const tombolSimpan = document.querySelector('form button[type="submit"]');
```

---

## 📝 2. Ubah Konten (Mengganti Isi Teks)
Mengubah tulisan yang ada di layar.

### 📐 Rumus / Syntax
```javascript
elemen.innerText = "Teks Baru";
```
* **`innerText`**: Mengubah teks yang terlihat. (Aman).
* **`innerHTML`**: Mengubah HTML (Bisa masukin `<b>` atau `<div>`). Hati-hati rawan di-hack (XSS).

### 🧪 Contoh (Update Saldo):
HTML: `<span id="angka-saldo">0</span>`
```javascript
const saldoDisplay = document.querySelector('#angka-saldo');
let saldoBaru = 50000;

// JS menyuruh HTML ganti angka
saldoDisplay.innerText = `Rp ${saldoBaru}`; 
// Hasil di layar: "Rp 50000"
```

---

## 🎨 3. Ubah Gaya (Ganti Baju CSS)
JS bisa mengubah CSS secara langsung (Inline Style).

### 📐 Rumus / Syntax
```javascript
elemen.style.propertiCSS = "nilai";
```
* **Aturan Penting:** Properti CSS yang ada stripnya (`-`) harus diubah jadi **camelCase**.
    * `background-color` ❌ -> `backgroundColor` ✅
    * `font-size` ❌ -> `fontSize` ✅

### 🧪 Contoh (Peringatan Saldo Habis):
```javascript
const kotakPesan = document.querySelector('.pesan-error');

// Ubah warna teks jadi merah
kotakPesan.style.color = "red";

// Ubah ukuran font
kotakPesan.style.fontSize = "20px";

// Sembunyikan elemen (display: none)
kotakPesan.style.display = "none";
```

---

## 👂 4. Event Listener (Pasang Kuping)
Membuat elemen "Peka" terhadap sentuhan user.

### 📐 Rumus Dasar
```javascript
elemen.addEventListener('jenis_kejadian', (event) => {
  // Aksi yang dilakukan saat kejadian terjadi
});
```

### A. Event `click` (Klik Tombol) 🖱️
#### 🧪 Contoh:
HTML: `<button id="btn-jajan">Beli</button>`
```javascript
const tombol = document.querySelector('#btn-jajan');

tombol.addEventListener('click', () => {
  console.log("Tombol diklik!");
  alert("Berhasil Jajan!");
});
```

### B. Event `submit` (Kirim Formulir) 📝
**PENTING:** Form punya sifat alami me-refresh halaman saat dikirim. Kita harus mencegahnya pakai `event.preventDefault()`.

#### 🧪 Contoh:
HTML: `<form id="form-transaksi">...</form>`
```javascript
const form = document.querySelector('#form-transaksi');

form.addEventListener('submit', (event) => {
  // 1. CEGAH browser refresh halaman (WAJIB BUAT FORM)
  event.preventDefault(); 
  
  // 2. Ambil data, hitung, dll...
  console.log("Data tersimpan, halaman tidak refresh!");
});
```