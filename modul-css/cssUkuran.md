# 📏 Kitab Suci CSS: Satuan Ukuran (Units)

> **Pesan Tante:** Jangan semuanya pakai `px`! Dunia ini tidak selebar layar laptopmu doang.

## 1. Kubu Kaku (Absolute Units) 🗿
Satuan yang nilainya TETAP, tidak peduli ukuran layar, tidak peduli settingan browser.

### `px` (Pixels)
* **Apa itu?** Titik terkecil di layar.
* **Sifat:** Keras kepala. Kalau kamu set `font-size: 16px`, dia akan selamanya 16px. Mau di layar bioskop atau layar jam tangan, dia tetap segitu.
* **Kapan Dipakai?**
    * Untuk ketebalan garis (`border: 1px`).
    * Untuk bayangan (`box-shadow: 4px`).
    * Untuk ukuran gambar yang memang harus pas segitu (misal logo kecil).
* **Kapan DILARANG?**
    * **JANGAN PAKAI `px` BUAT FONT (Teks)!** Kenapa? Kalau user matanya minus dan dia ubah settingan browser jadi "Large Text", webmu gak bakal berubah. Kamu mendiskriminasi orang berkacamata!

---

## 2. Kubu Karet (Relative Units) 🪀
Satuan yang nilainya BERUBAH-UBAH tergantung acuan lain. Ini kunci **Responsive Design**.

### `rem` (Root EM) - ⭐ ANAK EMAS TANTE
* **Acuan:** Ukuran font bawaan browser (Root).
* **Rumus:** Standarnya, **1rem = 16px**.
* **Kenapa Bagus?** Kalau user set browsernya ke "Large Text" (misal jadi 20px), maka `1rem` di webmu otomatis jadi 20px. Webmu menghargai pilihan user.
* **Saran Tante:** Gunakan `rem` untuk **Font Size**, **Padding**, dan **Margin**.

### `em` (Element EM) - ⚠️ SI PENGACAU
* **Acuan:** Ukuran font **INDUKNYA** (Parent).
* **Sifat:** Berbahaya buat pemula. Dia punya efek "bunga berbunga" (Compounding).
    * Contoh: Kalau induknya 20px, maka `1em` anaknya = 20px. Kalau di dalam anak itu ada cucu pakai `1em` lagi, dia ngikut bapaknya. Bisa pusing ngitungnya.
* **Saran Tante:** Hindari dulu `em` kecuali kamu tahu persis apa yang kamu lakukan. Pakai `rem` saja, lebih stabil.

### `%` (Persen)
* **Acuan:** Ukuran wadah **INDUKNYA** (Parent).
* **Contoh:**
    * Kamu punya kotak `width: 500px`.
    * Di dalamnya ada anak `width: 50%`.
    * Maka lebar anak = 250px.
* **Kapan Dipakai?** Sangat bagus buat layout kolom.

---

## 3. Kubu Layar (Viewport Units) 📺
Satuan yang acuannya adalah **Ukuran Jendela Browser** (Layar Monitor/HP).

### `vw` (Viewport Width)
* **Acuan:** Lebar layar.
* **Rumus:** `100vw` = 100% lebar layar mentok kiri ke kanan. `50vw` = Setengah lebar layar.
* **Bedanya sama `%`?**
    * `%` ngikutin lebar Induk (bisa kecil kalau induknya kecil).
    * `vw` ngikutin layar monitor (selalu besar/kecil sesuai jendela).

### `vh` (Viewport Height)
* **Acuan:** Tinggi layar.
* **Rumus:** `100vh` = 100% tinggi layar yang terlihat saat ini.
* **Kapan Dipakai?**
    * Sering banget dipakai buat **Hero Section** (Bagian paling atas web).
    * `height: 100vh;` artinya: "Tolong kotak ini tingginya memenuhi satu layar penuh, gak peduli layarnya HP atau TV."

### `vmin` & `vmax` (Jarang Dipakai)
* `vmin`: Pilih mana yang lebih kecil antara lebar atau tinggi layar.
* `vmax`: Pilih mana yang lebih besar.

---

## 🧪 Ringkasan Praktik Terbaik (Cheat Sheet)

| Mau Mengatur Apa? | Pakai Satuan Apa? | Alasan Tante |
| :--- | :--- | :--- |
| **Ukuran Huruf (Font)** | `rem` | Biar aksesibel & bisa di-zoom. |
| **Jarak (Margin/Padding)** | `rem` atau `px` | `rem` biar proporsional, `px` kalau mau fix. |
| **Lebar Layout (Width)** | `%` atau `max-width` | Biar responsif di HP. |
| **Tinggi Banner Utama** | `vh` | Biar pas satu layar penuh. |
| **Garis Tepi (Border)** | `px` | Garis 1px selalu terlihat tajam. |
| **Media Query (Breakpoint)**| `px` / `em` | Misal: `@media (max-width: 768px)` |