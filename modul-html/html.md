# 📑 Rangkuman Anatomi Tag HTML 

> **Status:** Materi Dasar Web Dev
> **Sumber:** MDN Web Docs & HTML Living Standard

## 📊 Statistik Tag (Estimasi 2026)
* **Total Pernah Ada:** ± 142 Tag
* **Valid & Berguna:** ± 115 Tag (Fokus di sini!)
* **Sampah (Obsolete):** ± 27 Tag (Jangan disentuh!)

---

## 🏗️ Kasta Tag HTML

### 1. Kasta "Zombie" 🧟 (HARAM DIPAKAI!)
Tag jadul yang sudah mati. Kalau dipakai, kode jadi kotor dan tidak profesional.
* `marquee` (Teks jalan)
* `center` (Tengahin teks -> Ganti pakai CSS!)
* `font` (Atur huruf -> Ganti pakai CSS!)
* `blink` (Kelap-kelip)

### 2. Kasta "Raja & Ratu" 👑 (Struktur Mutlak)
Wajib ada di setiap file HTML.
* `<html>`: Pembungkus utama.
* `<head>`: Otak (meta data, judul, link CSS).
* `<body>`: Badan (isi yang tampil di layar).

### 3. Kasta "Penyelamat Semantik" 🛡️ (HTML5 Modern)
Gunakan ini agar website disukai Google (SEO) dan mudah dibaca screen reader.
* **Navigasi:** `<nav>`
* **Kepala/Kaki:** `<header>`, `<footer>`
* **Isi Utama:** `<main>`, `<article>`, `<section>`
* **Sampingan:** `<aside>`

### 4. Kasta "Interaktif & Media" 🎮
* **Media:** `<img>`, `<video>`, `<audio>`
* **Input User:** `<form>`, `<input>`, `<button>`, `<textarea>`
* **Grafis:** `<svg>`, `<canvas>`

### 5. Kasta "Generik" 📦 (Wadah Kosong)
Pakai hanya jika tidak ada tag semantik yang cocok.
* `<div>`: Wadah besar (Block).
* `<span>`: Wadah kecil (Inline).

---

> **Pesan Moral:** Jangan jadi developer yang kena penyakit *Div-itis* (sedikit-sedikit pakai div). Gunakan tag sesuai fungsinya!