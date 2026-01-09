# 📜 KITAB PENGGUNAAN SATUAN CSS

## 1. 👑 rem (Root EM)
> *"Si Raja Teks & Spasi"*

### KAPAN DIPAKAI?
* ✅ **`font-size` (WAJIB):** Untuk semua ukuran huruf.
* ✅ **`margin` & `padding` (Layout Utama):** Untuk jarak antar-div atau jarak container besar.
* ✅ **`width` / `height` (Fixed):** Kalau kamu butuh ukuran elemen yang tetap tapi mau tetap fleksibel kalau user nge-zoom.

**ALASAN:** Biar website-mu konsisten dan ramah aksesibilitas (ikut settingan font HP user).
**TRIK SAKTI:** Ingat `html { font-size: 62.5%; }` biar `1rem = 10px`.

---

## 2. 👪 em (Relative to Parent)
> *"Si Spesialis Komponen"*

### KAPAN DIPAKAI?
* ✅ **`padding` (Di dalam Tombol/Badge):** Biar jarak dalam tombolnya membesar otomatis kalau teksnya membesar.
* ✅ **`margin` (Di sekitar Icon + Teks):** Biar jarak icon ke teks selalu proporsional.

### JANGAN DIPAKAI UNTUK:
* ⛔ **`font-size`:** Bahaya! Bisa beranak-pinak jadi raksasa kalau elemennya bersarang (*nested*).

---

## 3. 🌊 % (Persen)
> *"Si Pengatur Lebar"*

### KAPAN DIPAKAI?
* ✅ **`width` & `max-width`:** Untuk membagi layout. Misal: Sidebar 30%, Konten 70%.
* ✅ **Gambar Responsif:** `img { width: 100%; }` biar gambar gak nabrak keluar layar HP.

**ALASAN:** Biar layoutnya "cair" (*fluid*) menyesuaikan lebar layar apapun.

---

## 4. 🔨 px (Pixel)
> *"Si Detail Tajam"*

### KAPAN DIPAKAI?
* ✅ **`border`:** `1px solid black`. Garis tipis butuh ketajaman pixel.
* ✅ **`box-shadow`:** Bayangan butuh ukuran pasti.
* ✅ **`border-radius` (Kecil):** Misal `4px` untuk sudut kartu yang halus.
* ✅ **Media Query Breakpoints:** `@media (max-width: 768px)` (Walaupun sekarang banyak yang mulai pakai `em`/`rem` di sini juga, tapi `px` masih standar umum).

---

## 5. 📺 vh & vw (Viewport)
> *"Si Penguasa Layar"*

### KAPAN DIPAKAI?
* ✅ **`height`:** `100vh` (Khusus untuk Hero Section / Halaman Depan Full Screen).
* ✅ **`width`:** `100vw` (Kalau mau elemen maksa memenuhi layar walaupun ada parent yang membatasi).