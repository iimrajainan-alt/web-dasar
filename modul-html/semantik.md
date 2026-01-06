# 🛡️ Anatomi HTML Semantik (Biar Disayang Google)

> **May Prinsip:** Jangan pakai `<div>` kalau ada tag yang lebih spesifik. `<div>` itu cuma opsi terakhir (darurat).

---

## 1. Struktur Luar (Kerangka Badan)

### `<header>` (Kepala/Topi) 🎩
* **Fungsi:** Wadah untuk pembukaan atau navigasi.
* **Isinya:** Biasanya Logo, Judul Website, atau Menu Navigasi.
* **Posisi:** Gak harus selalu di paling atas halaman. Sebuah `<article>` juga bisa punya `<header>` sendiri (judul artikel).

### `<nav>` (Kompas/Peta) 🧭
* **Fungsi:** Wadah khusus untuk **LINK NAVIGASI** utama.
* **Kapan Dipakai:** Menu Home/About/Contact, Daftar Isi.
* **Kapan JANGAN Dipakai:** Tombol "Buy Now" atau link medsos di footer (itu cuma link biasa, bukan navigasi utama).

### `<main>` (Daging Utama) 🥩
* **Fungsi:** Wadah konten **UNIK** di halaman tersebut.
* **Aturan Keras:** Cuma boleh ada **SATU** `<main>` per halaman.
* **Isinya:** Artikel blognya, Form loginnya, atau Daftar produknya. (Sidebar dan Footer JANGAN masuk sini).

### `<footer>` (Kaki/Sepatu) u1F45F
* **Fungsi:** Penutup halaman atau bagian.
* **Isinya:** Hak cipta (Copyright), kontak info, peta lokasi, link sitemap.

---

## 2. Struktur Dalam (Pengatur Konten)

### `<section>` (Bab Buku) 📑
* **Fungsi:** Mengelompokkan konten yang **Satu Tema**.
* **Syarat:** Biasanya punya Judul sendiri (`<h2>` - `<h6>`).
* **Contoh:** Bagian "Testimoni", Bagian "Fitur Produk", Bagian "Hubungi Kami".

### `<article>` (Postingan Koran) 📰
* **Fungsi:** Konten yang **Berdiri Sendiri (Independent)**.
* **Tes Logika:** Kalau bagian ini kamu gunting lalu tempel di koran lain atau kirim via WA, apakah isinya masih masuk akal?
    * ✅ Masih masuk akal -> Pakai `<article>` (Contoh: Berita, Post Blog, Komentar User, Kartu Produk).
    * ❌ Jadi aneh/kurang konteks -> Pakai `<section>`.

### `<aside>` (Bisikan Tetangga) 🗣️
* **Fungsi:** Konten pendukung yang **Tidak Terlalu Penting** (Sampingan).
* **Isinya:** Sidebar, Iklan Banner, "Artikel Terkait", atau Bio Penulis di samping artikel.
* **Posisi:** Kalau dihapus, konten utama (`<main>`) tetap bisa dipahami.

---

## 3. Contoh Penerapan (Anatomi Manusia)

Bayangkan halaman web itu seperti tubuh manusia:

```html
<body>

  <header>
    <h1>Dompet App</h1> <nav>
      <a href="#">Home</a>
      <a href="#">Saldo</a>
      <a href="#">Profil</a>
    </nav>
  </header>

  <main>
    
    <section id="saldo-box">
      <h2>Saldo Anda</h2>
      <p>Rp 5.000.000</p>
    </section>

    <section id="transaksi-terbaru">
      <h2>Riwayat Jajan</h2>
      
      <article class="kartu-transaksi">
        <h3>Beli Seblak</h3>
        <p>Harga: Rp 15.000</p>
        <span class="tanggal">Senin, 10 Jan</span>
      </article>

      <article class="kartu-transaksi">
        <h3>Bayar Kos</h3>
        <p>Harga: Rp 800.000</p>
      </article>
      
    </section>

  </main>

  <aside>
    <h3>Promo Hari Ini</h3>
    <p>Diskon Top Up 50%!</p>
  </aside>

  <footer>
    <p>&copy; 2026 Dompet App by Maba.</p>
  </footer>

</body>
```