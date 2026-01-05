# 🎨 Kitab Suci CSS: Jurusan Desain Grafis (Visual)

> **Filosofi Tante:** Web yang cantik itu web yang *readable* (mudah dibaca) dan *accessible* (nyaman di mata). Jangan norak!

## 1. Typography (Seni Mengolah Huruf) 🔤
Ini paling vital. 90% isi web adalah teks. Kalau teksmu jelek, orang malas baca.

### `font-family`
* **Fungsi:** Memilih jenis font.
* **Aturan:** Selalu sediakan cadangan (*fallback*).
* **Contoh:** `font-family: 'Poppins', Helvetica, sans-serif;`
    * Artinya: "Coba pakai Poppins. Kalau gak ada, pakai Helvetica. Kalau gak ada juga, pakai font bawaan laptop yang gak ada kakinya (sans-serif)."
* **Tips:** Hindari Times New Roman (default) kecuali kamu bikin koran. Pakai *Sans-Serif* (Arial, Roboto, Inter) buat tampilan modern.

### `font-size`
* **Fungsi:** Ukuran huruf.
* **Satuan Wajib:**
    * `px`: Kaku. (Misal `16px`).
    * `rem`: **Sangat Disarankan!** Mengikuti setelan browser user. (Biasanya `1rem` = `16px`). Ramah aksesibilitas.

### `font-weight`
* **Fungsi:** Ketebalan huruf.
* **Nilai:**
    * `400` = Normal/Regular.
    * `700` = **Bold** (Tebal).
    * `300` = Light (Tipis).

### `text-align`
* **Fungsi:** Perataan teks.
* **Nilai:** `left` (standar), `center` (judul), `right`, `justify` (rata kiri-kanan, hati-hati kadang jadi bolong-bolong).

### `line-height`
* **Fungsi:** Jarak antar baris (spasi ke bawah).
* **PENTING:** Kalau ini kekecilan, teks jadi dempet susah dibaca.
* **Standar Bagus:** `1.5` atau `1.6` (Artinya 1.5 kali ukuran hurufnya).

### `text-decoration`
* **Fungsi:** Hiasan garis pada teks.
* **Nilai:**
    * `underline`: Garis bawah (otomatis ada di Link `<a>`).
    * `none`: **Wajib** dipakai kalau mau menghilangkan garis bawah pada Link biar rapi.
    * `line-through`: Coretan (biasanya buat harga diskon).

### `text-transform`
* **Fungsi:** Mengubah kapitalisasi tanpa ganti isi HTML.
* **Nilai:** `uppercase` (CAPSLOCK SEMUA), `lowercase` (kecil semua), `capitalize` (Huruf Depan Besar).

---

## 2. Color & Background (Warna-Warni Kehidupan) 🖌️

### `color`
* **Fungsi:** Warna **TEKS** (Ingat! Cuma `color`, bukan `font-color`).
* **Format Warna:**
    * Keyword: `red`, `blue`, `black` (Terbatas).
    * Hex: `#FF0000` (Paling umum).
    * RGB/RGBA: `rgba(0, 0, 0, 0.5)` (Hitam dengan transparansi 50%).

### `background-color`
* **Fungsi:** Warna latar belakang kotak.
* **Tips:** Pastikan kontras! Kalau background gelap, teks HARUS terang. Jangan background hitam teks biru tua, itu dosa besar.

### `background-image`
* **Fungsi:** Pasang gambar sebagai latar.
* **Syntax:** `background-image: url('gambar.jpg');`
* **Temannya (Wajib Ada):**
    * `background-size: cover;` (Biar gambar menutupi kotak dengan rapi tanpa gepeng).
    * `background-position: center;` (Biar fokus gambar di tengah).
    * `background-repeat: no-repeat;` (Biar gambar gak berulang-ulang kayak ubin).

### `opacity`
* **Fungsi:** Transparansi elemen (Hantu mode).
* **Nilai:** `0` (Hilang) sampai `1` (Nyata).
* **Efek Samping:** Kalau induknya transparan (`0.5`), anaknya IKUTAN transparan. Kalau mau background doang yang transparan, pakai `background-color: rgba(...)`.

---

## 3. Decoration (Kosmetik & Aksesoris) 💄
Biar webmu gak kotak-kotak kaku kayak web tahun 90-an.

### `border-radius`
* **Fungsi:** Menumpulkan sudut kotak yang tajam.
* **Nilai:**
    * `4px` - `8px`: Tumpul manis (estetik modern).
    * `50%`: Mengubah kotak persegi menjadi **LINGKARAN** sempurna (biasanya buat foto profil).

### `box-shadow`
* **Fungsi:** Memberi bayangan biar elemen terlihat "mengambang" (3D).
* **Syntax:** `offset-x offset-y blur-radius color`.
* **Contoh:** `box-shadow: 0 4px 10px rgba(0,0,0,0.1);` (Bayangan halus di bawah).
* **Tips:** Jangan pakai bayangan hitam pekat! Pakai abu-abu transparan biar elegan.

### `cursor`
* **Fungsi:** Mengubah bentuk mouse saat diarahkan ke elemen.
* **Nilai:**
    * `pointer`: Jari telunjuk 👆 (Wajib buat tombol/link).
    * `not-allowed`: Tanda dilarang 🚫 (Buat tombol disable).
    * `text`: Garis lurus I (Buat input teks).

---

## 4. Object Fit (Khusus Gambar `<img>`) 🖼️
Pernah masukin gambar ke kotak tapi gambarnya jadi gepeng/penyet? Ini solusinya.

### `object-fit`
* **Fungsi:** Mengatur bagaimana gambar `<img>` menyesuaikan diri dengan `width` dan `height` pembungkusnya.
* **Nilai:**
    * `cover`: **Paling Sakti!** Gambar akan di-zoom dan dipotong sedikit biar pas memenuhi kotak TANPA gepeng.
    * `contain`: Gambar mengecil biar muat seutuhnya (ada sisa ruang kosong).# 🎨 Kitab Suci CSS: Jurusan Desain Grafis (Visual)

> **Filosofi Tante:** Web yang cantik itu web yang *readable* (mudah dibaca) dan *accessible* (nyaman di mata). Jangan norak!