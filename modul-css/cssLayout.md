# 🏗️ Kitab Suci CSS: Jurusan Tukang Bangunan (Layout)

> **Peringatan Tante:** Ini adalah properti yang WAJIB dimengerti luar kepala. Jangan cuma copas, pahami logikanya!

## 1. The Box Model (Fondasi Rumah) 📦
Setiap elemen HTML adalah kotak. Properti ini mengatur ukuran dan "daging" kotak tersebut.

### `width` & `height`
* **Fungsi:** Mengatur lebar dan tinggi.
* **Satuan Wajib Tahu:**
    * `px`: Pasti (misal: 100px). Kaku.
    * `%`: Relatif terhadap induknya (misal: 50% dari layar).
    * `rem`: Mengikuti ukuran font root (bagus buat responsif).
    * `vh` / `vw`: Persen dari tinggi/lebar layar monitor (Viewport).

### `padding`
* **Fungsi:** Jarak **DI DALAM** kotak (antara isi dan garis tepi).
* **Efek:** Bikin kotak jadi gembung/gemuk.
* **Analogi:** Lemak tubuh atau jaket tebal yang kamu pakai.

### `margin`
* **Fungsi:** Jarak **DI LUAR** kotak (antara elemen ini dengan elemen tetangga).
* **Efek:** Memberi ruang napas, menolak elemen lain menjauh.
* **Trik:** `margin: 0 auto;` (Jurus klasik bikin kotak jadi rata tengah horizontal).

### `border`
* **Fungsi:** Garis tepi/pagar pembatas.
* **Shorthand:** `border: 2px solid black;` (Tebal, Tipe Garis, Warna).

### 🚨 `box-sizing: border-box;` (PENTING!)
* **Masalah:** Secara default, kalau kamu kasih `width: 100px` + `padding: 20px`, total lebar jadi 140px. Matematika hancur!
* **Solusi:** Pasang `box-sizing: border-box;`.
* **Efek:** `padding` dan `border` akan memakan bagian dalam, ukuran total TETAP 100px.
* **Saran Tante:** Selalu taruh ini di paling atas CSS-mu (`* { box-sizing: border-box; }`).

### Position (Jurus Melayang) 🎈
* **`static`**: Diam (Default).
* **`relative`**: Diam, tapi jadi patokan koordinat buat anaknya yang `absolute`.
* **`absolute`**: Melayang bebas, keluar dari aliran normal, nempel ke induk `relative`.
* **`fixed`**: Nempel di layar monitor (kayak Navbar).

---

## 2. Display (Jati Diri Elemen) 🎭
Menentukan bagaimana elemen berperilaku di tengah kerumunan.

* `display: block;`
    * Sifat: **Egois**. Memakan satu baris penuh (lebar 100%). Elemen lain diusir ke bawah.
    * Contoh: `<div>`, `<p>`, `<h1>`.
* `display: inline;`
    * Sifat: **Sosial**. Lebarnya cuma seukuran isinya. Bisa duduk sebelahan. Gak bisa diatur margin atas-bawahnya.
    * Contoh: `<span>`, `<a>` (link).
* `display: inline-block;`
    * Sifat: **Hybrid**. Bisa sebelahan (inline), tapi bisa diatur ukurannya (block).
* `display: none;`
    * Sifat: **Ninja**. Hilang dari layar, tidak memakan tempat sama sekali.

---

## 3. Flexbox (Jurus Tata Letak Modern) 💪
Lupakan `float`. Pakai ini buat mengatur posisi anak-anak elemen dalam satu baris/kolom.

### Di Wadah Induk (Parent Container):
1.  `display: flex;`: Wajib. Mengaktifkan mode Flexbox.
2.  `flex-direction`:
    * `row` (Default): Anak berbaris ke samping (kiri-kanan).
    * `column`: Anak berbaris ke bawah (atas-bawah).
3.  `justify-content` (Sumbu Utama/X):
    * `flex-start`: Rata kiri.
    * `center`: Rata tengah.
    * `flex-end`: Rata kanan.
    * `space-between`: Anak pertama di ujung kiri, anak terakhir di ujung kanan, sisanya nyebar.
4.  `align-items` (Sumbu Silang/Y):
    * `center`: Pas di tengah vertikal (Jurus Anti Pusing nengahin teks).
    * `stretch`: Ditarik biar tingginya sama semua.
5.  `gap`:
    * Memberi jarak antar anak tanpa pusing ngitung margin. (Contoh: `gap: 20px;`).

---

## 4. Grid (Cetak Biru Halaman) 🏁
Lebih sakti dari Flexbox buat bikin layout 2 dimensi (baris DAN kolom sekaligus).

### Di Wadah Induk:
1.  `display: grid;`: Aktifkan mode Grid.
2.  `grid-template-columns`:
    * Membagi kolom.
    * Contoh: `1fr 1fr 1fr` (Bikin 3 kolom sama rata). `fr` artinya "fraction" (bagian).
    * Contoh: `200px 1fr` (Kolom kiri 200px, kolom kanan sisanya).
3.  `gap`: Jarak antar kotak (selokan).

---

## 5. Position (Jurus Melayang) 🎈
Mengeluarkan elemen dari aliran normal dokumen.

* `position: static;` (Default): Posisi normal, nurut aturan, gak bisa digeser paksa.
* `position: relative;`: Masih di tempat aslinya, tapi bisa digeser dikit (`top`, `left`) tanpa ganggu tetangga. Biasanya jadi patokan buat anak yang `absolute`.
* `position: absolute;`:
    * **Anak Durhaka**. Dia keluar dari aliran normal, melayang, dan menempel pada **Induk Terdekat yang Relative**.
    * Bisa ditaruh di mana aja (misal: pojok kanan atas kartu).
* `position: fixed;`:
    * **Benalu Layar**. Nempel terus di layar monitor walau di-scroll. (Contoh: Navbar atau tombol Chat WA).
* `position: sticky;`:
    * **Bunglon**. Awalnya normal, pas di-scroll sampai titik tertentu, dia jadi nempel (fixed).

### `z-index`
* Menentukan tumpukan (layer).
* Angka makin besar = makin di atas/depan.
* Syarat: `position` tidak boleh `static`.

---

## 6. Overflow (Ember Tumpah) 🪣
Apa yang terjadi kalau isinya lebih besar dari wadahnya?

* `overflow: visible;` (Default): Tumpah ke luar, nembus batas kotak (Jelek!).
* `overflow: hidden;`: Yang tumpah dipotong/disembunyikan.
* `overflow: scroll;`: Muncul scrollbar biar bisa digeser.
* `overflow: auto;`: Muncul scrollbar HANYA jika isinya kepentok. (Paling aman).