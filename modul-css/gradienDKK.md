# 🎨 Kitab Visual Efek: Gradient, Shadow & Glass (+ Penjelasan Logika)

> **Status:** Bedah Anatomi CSS
> **May Prinsip:** Jangan cuma hafal kodenya, pahami bagaimana browser "melukis" pikselnya.

---

## 🌈 1. Anatomi Gradient (Melukis dengan Matematika)
Browser menganggap gradient sebagai **Gambar**, bukan Warna. Makanya propertinya `background-image` atau `background` (shorthand), bukan `background-color`.

### A. Linear Gradients (Garis Lurus)
Logikanya: Menarik garis lurus imajiner, lalu menaruh titik-titik warna di sepanjang garis itu.

**Rumus:** `linear-gradient(ARAH, WARNA-1 POSISI, WARNA-2 POSISI)`

**1. The Startup Blue (Biru Modern)**
```css
/* 90deg = Garis ditarik dari Kiri ke Kanan. */
/* 0% = Warna #00C9FF mulai dari ujung paling kiri. */
/* 100% = Warna #92FE9D berakhir di ujung paling kanan. */
background: linear-gradient(90deg, #00C9FF 0%, #92FE9D 100%);
```

**2. Warm Sunset (Senja Hangat)**
```css
/* 135deg = Garis diagonal dari Kiri-Atas ke Kanan-Bawah. */
/* Ini sudut paling favorit desainer karena terasa natural (seperti cahaya matahari sore). */
background: linear-gradient(135deg, #F5576C 0%, #F093FB 100%);
```

**3. Midnight Purple (Gelap Elegan)**
```css
/* Tanpa sudut = Default (Dari Atas ke Bawah). */
/* Cocok untuk background body biar gak bosan hitam polos. */
background: linear-gradient(#2E3192, #1BFFFF);
```

**4. Complex Trio (Tiga Warna)**
```css
/* Kamu bisa masukkan warna sebanyak mungkin. */
/* 50% di tengah artinya warna kuning (#FFFB7D) benar-benar dominan di titik tengah elemen. */
background: linear-gradient(45deg, #85FFBD 0%, #FFFB7D 50%, #ffffff 100%);
```

### B. Radial Gradients (Lingkaran)
Logikanya: Menjatuhkan cat di tengah, lalu menyebar ke luar.

**Rumus:** `radial-gradient(BENTUK, WARNA-DALAM, WARNA-LUAR)`

**1. Spotlight (Sorotan Cahaya)**
```css
/* 'circle' memaksa bentuk bulat sempurna (kalau tidak, dia jadi elips mengikuti kotak). */
/* 74% artinya warna abu-abu baru mulai dominan di 74% jarak dari pusat. */
background: radial-gradient(circle, #ffffff 0%, #d7e1ec 74%);
```

### C. Conic Gradients (Jam Dinding) 🥧
Logikanya: Melukis berputar searah jarum jam dilihat dari atas (Top Down View).

**1. Color Wheel (Roda Warna)**
```css
/* Sering dipakai untuk border pelangi yang bergerak atau diagram pie. */
background: conic-gradient(red, yellow, lime, aqua, blue, magenta, red);
```

### D. Text Gradient (Teknik Topeng) 🔥
Ini bukan fitur standar, ini **HACK**. Kita menumpuk background di atas teks, lalu memotong background itu sesuai bentuk hurufnya.

**1. Gold Effect (Emas)**
```css
/* 1. Bikin background emas dulu */
background: linear-gradient(to right, #BF953F, #FCF6BA, #B38728, #FBF5B7, #AA771C);

/* 2. POTONG backgroundnya mengikuti bentuk huruf (Clip). */
-webkit-background-clip: text;
background-clip: text;

/* 3. Bikin warna teks ASLI jadi transparan. */
/* Kalau teksnya masih hitam, background emas di belakangnya gak bakal kelihatan! */
color: transparent;
```

---

## 👻 2. Anatomi Box Shadow (Ilusi Cahaya)
Shadow itu mensimulasikan jarak benda dari lantai. Makin jauh/blur shadow, makin "tinggi" benda melayang.

**Rumus:** `offset-x | offset-y | blur-radius | spread-radius | color`

### A. Soft Shadow (Prinsip Cahaya Lembut)
Rahasianya ada di **Blur Radius** yang besar dan **Alpha (Transparansi)** yang kecil.

**1. Elevation Low (Melayang Dikit)**
```css
/* x=0 (cahaya dari atas tegak lurus), y=2 (bayangan turun dikit). */
/* Blur 8px bikin pinggiran bayangan halus. */
/* Opacity 0.1 (10%) bikin bayangan tidak pekat/kotor. */
box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
```

**2. Elevation High (Melayang Tinggi)**
```css
/* Teknik Double Shadow: */
/* Layer 1: Bayangan besar & jauh (20px 25px) untuk kesan melayang. */
/* Layer 2: Bayangan kecil & dekat (10px 10px) untuk kesan ada volume di dekat benda. */
box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 
            0 10px 10px -5px rgba(0, 0, 0, 0.04);
```

### B. Colored Shadow (Glow Effect) ✨
Bayangan hitam bikin warna kusam. Bayangan berwarna bikin benda "hidup".

**1. Blue Glow**
```css
/* Rahasianya: Warna shadow SAMA dengan warna tombol, tapi transparansinya diturunkan (0.39). */
box-shadow: 0 4px 14px 0 rgba(0, 118, 255, 0.39);
```

### C. Neumorphism (Efek Cahaya Timbul) 🗿
Ini mainan ilusi optik. Kita butuh **Dua Bayangan**:
1. Bayangan Gelap di pojok kanan-bawah (Bayangan benda).
2. Bayangan Putih/Terang di pojok kiri-atas (Highlight cahaya).

**1. Flat/Extruded (Timbul)**
```css
/* Bayangan Gelap (Kanan Bawah) */
box-shadow: 9px 9px 16px rgb(163,177,198,0.6), 
/* Highlight Putih (Kiri Atas - makanya nilainya negatif -9px) */
           -9px -9px 16px rgba(255,255,255, 0.5);
```

**2. Pressed/Inset (Tenggelam)**
```css
/* Kata kunci 'inset' memindahkan bayangan ke DALAM kotak. */
/* Hasilnya kotak terlihat cekung ke dalam seperti tombol ditekan. */
box-shadow: inset 6px 6px 10px 0 rgba(163,177,198, 0.7), 
            inset -6px -6px 10px 0 rgba(255,255,255, 0.8);
```

---

## 🧊 3. Anatomi Glassmorphism (Kaca Buram)
Efek ini bekerja dengan memanipulasi piksel yang ada **DI BELAKANG** elemen tersebut.

**1. The Perfect Glass (Resep Standar)**
```css
/* 1. Background WAJIB semi-transparan. */
/* Kalau background: #fff (solid), kita gak bisa lihat apa-apa di belakangnya. */
background: rgba(255, 255, 255, 0.25);

/* 2. THE MAGIC: backdrop-filter. */
/* Beda dengan 'filter' (yang memburamkan elemennya sendiri), */
/* 'backdrop-filter' memburamkan APAPUN yang ada di balik kaca ini. */
backdrop-filter: blur(10px);
-webkit-backdrop-filter: blur(10px); /* Safari butuh ini biar jalan. */

/* 3. Border Tipis Transparan */
/* Ini mensimulasikan pantulan cahaya di pinggiran kaca tebal. */
border: 1px solid rgba(255, 255, 255, 0.18);

/* 4. Shadow Halus */
/* Memberi jarak antara kaca dan background belakangnya. */
box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);

border-radius: 16px;
```