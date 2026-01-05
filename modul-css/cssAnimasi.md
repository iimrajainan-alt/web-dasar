## 🎬 BAGIAN 4: ANIMATOR (Motion & Transform)
Membuat benda bergerak. Ingat performa!

### 1. Transform: Translate X & Y (Koordinat) 📍
Ini yang kamu tanyakan! Menggeser elemen tanpa mengganggu elemen lain.

* **Sistem Koordinat Web:**
    * Titik `0,0` ada di **POJOK KIRI ATAS** elemen.
    * **Sumbu X (Horizontal):** Kiri (-) ⟷ Kanan (+).
    * **Sumbu Y (Vertikal):** Atas (-) ⟷ Bawah (+). **(⚠️ INI KEBALIKAN MATEMATIKA SEKOLAH!)**

* **`translateX(nilai)`**: Geser Kiri/Kanan.
    * `translateX(50px)`: Geser ke **KANAN** 50px.
    * `translateX(-50px)`: Geser ke **KIRI** 50px.

* **`translateY(nilai)`**: Geser Atas/Bawah.
    * `translateY(20px)`: Geser ke **BAWAH** 20px.
    * `translateY(-20px)`: Geser ke **ATAS** 20px. (Sering dipakai buat efek tombol melayang naik).

* **`translate(x, y)`**: Gabungan.
    * `translate(10px, -10px)`: Geser Kanan 10px, Naik 10px.

* **Fungsi Lain:**
    * `rotate(deg)`: Memutar.
    * `rotate(90deg)`: Putar 90 derajat.
    * Contoh: `transform: rotate(45deg);` (Miring 45 derajat).
    * `scale(n)`: Membesarkan/Mengecilkan.
    * Contoh: `transform: scale(1.2);` (Membesar 20%).
    * Contoh: `transform: scale(0.9);` (Mengecil dikit saat tombol ditekan).
     * `scale(1.1)`: Membesar 10%.
    

### 2. Transition (Transisi Halus) 🌊
Mengubah perubahan kasar menjadi mulus.
* Syntax: `transition: property duration timing-function;`
* Contoh: `transition: all 0.3s ease;`
* Taruh di *state* awal elemen, bukan di `:hover`.

### 3. Keyframes (Animasi Looping) 🎞️
Skenario film yang jalan sendiri.
```css
@keyframes naik-turun {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-10px); } /* Naik */
  100% { transform: translateY(0); }     /* Turun */
}

.hantu {
  animation: naik-turun 2s infinite ease-in-out;
}