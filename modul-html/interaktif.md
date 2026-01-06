# 🎮 Kasta Interaktif & Media: Bikin Web Hidup

> **May Prinsip:** Website itu komunikasi dua arah. Jangan cuma nyuruh user baca, kasih mereka cara buat nonton, dengar, dan ngirim data.

---

## 📸 1. Media (Gambar & Suara)
Biar webmu gak pucat isinya teks doang.

### `<img>` (Gambar)
Tag paling umum tapi sering salah dipakai.
* **Sifat:** *Void Element* (Gak punya tag penutup `</img>`, langsung tutup di situ).
* **Atribut Wajib:**
    * `src`: Lokasi file gambar (URL atau path folder).
    * **`alt` (PENTING!):** Teks pengganti kalau gambar gagal loading atau buat tuna netra. Kalau kosong, Tante marah!
* **Contoh:**
  ```html
  <img src="kucing.jpg" alt="Foto kucing lucu warna oranye" width="300">
  ```

### `<video>` & `<audio>` (Multimedia)
Pemutar video/musik bawaan browser.
* **Atribut Wajib:** `controls` (biar muncul tombol play/pause). Kalau lupa ini, videonya jalan tapi user gak bisa matiin!
* **Tips:** Selalu kasih teks di dalamnya sebagai cadangan kalau browser jadul gak support.
* **Contoh:**
  ```html
  <video src="tutorial-koding.mp4" controls width="500">
    Maaf, browser HP kentangmu gak support video ini.
  </video>
  ```

---

## 📝 2. Input User (Formulir)
Ini jantungnya aplikasi (kayak "Dompet"-mu). Tanpa ini, gak ada data masuk.

### `<form>` (Wadah Formulir)
Pembungkus semua inputan.
* **Fungsi:** Mengelompokkan data yang mau dikirim ke server.
* **Atribut:** `action` (kirim ke mana?) dan `method` (cara kirimnya? GET/POST).

### `<input>` (Si Bunglon 🦎)
Tag paling sakti. Bentuknya bisa berubah-ubah tergantung `type`-nya.
* **Sifat:** *Void Element* (Gak ada penutup).
* **Jenis-jenis `type`:**
    * `type="text"`: Kotak tulisan biasa (Nama).
    * `type="password"`: Tulisan jadi bulat-bulat (Rahasia).
    * `type="email"`: Wajib ada `@` (Validasi otomatis).
    * `type="number"`: Cuma bisa angka (Umur/Harga).
    * `type="checkbox"`: Centang banyak (Hobi).
    * `type="radio"`: Pilih satu (Jenis Kelamin).
    * `type="date"`: Kalender.
* **Contoh:**
  ```html
  <input type="email" placeholder="Masukan email..." required>
  ```

### `<textarea>` (Kotak Curhat)
Bedanya sama `input text`? Ini buat tulisan PANJANG & BANYAK BARIS.
* **Penting:** Punya tag penutup `</textarea>`.
* **Contoh:** Alamat lengkap, Komentar, Pesan cinta.

### `<button>` (Tombol Eksekusi)
Jangan pakai `<div>` buat tombol! Itu dosa aksesibilitas.
* **`type="submit"`**: Mengirim data form (Default di dalam form).
* **`type="button"`**: Tombol biasa (Biasanya buat dipasangin JavaScript).
* **Contoh:**
  ```html
  <button type="submit">Kirim Data</button>
  ```

---

## 🎨 3. Grafis (Gambar Kodingan)
Gambar yang dibuat bukan pakai kamera, tapi pakai kode.

### `<svg>` (Vektor - Scalable Vector Graphics)
* **Apa itu?** Gambar matematika (garis, kurva).
* **Kelebihan:** Di-zoom sampai sebesar baliho **GAK AKAN PECAH**. Ukuran file kecil.
* **Penggunaan:** Ikon, Logo, Ilustrasi datar.
* **Contoh:**
  ```html
  <svg width="100" height="100">
    <circle cx="50" cy="50" r="40" fill="red" />
  </svg>
  ```

### `<canvas>` (Kanvas Lukis JS)
* **Apa itu?** Area kosong yang gambarnya dimanipulasi pakai **JavaScript** per piksel.
* **Kelebihan:** Performanya kencang buat animasi berat.
* **Penggunaan:** Game web, Grafik data dinamis, Efek partikel.
* **Catatan:** HTML cuma nyiapin tempatnya, yang ngegambar itu JS.

---

## 🧪 Contoh Kasus: Form "Tambah Pengeluaran"
Coba terapkan ini di proyek Dompet-mu:

```html
<form action="/simpan-uang" method="POST">
  <label>Tanggal:</label>
  <input type="date" name="tanggal" required>
  <br>

  <label>Kategori:</label>
  <input type="radio" name="kategori" value="makan"> Makan
  <input type="radio" name="kategori" value="transport"> Transport
  <br>

  <label>Nominal (Rp):</label>
  <input type="number" name="jumlah" min="1000" placeholder="0">
  <br>

  <label>Catatan:</label>
  <textarea name="catatan" rows="3"></textarea>
  <br>

  <button type="submit">Simpan Pengeluaran</button>
</form>
```

> **Ingat May Pesan:**
> Selalu pasangkan `<input>` dengan `<label>` biar user tahu itu kotak buat ngisi apa. Jangan biarkan user menebak-nebak!