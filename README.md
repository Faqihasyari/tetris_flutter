# 🧩 Flutter Tetris Game

Proyek ini adalah implementasi game **Tetris klasik** menggunakan **Flutter**, dengan konsep **Provider State Management** dan **TickerProviderStateMixin** untuk animasi blok.  
Dibuat sebagai mini project pembelajaran logika game dan animasi di Flutter.

---


## 🚀 Fitur Utama
- Gameplay Tetris klasik (geser, putar, jatuh otomatis)
- Animasi lembut menggunakan `TickerProvider`
- Tampilan responsif (Next Piece, Score, Level)
- Pemisahan view: `LeftView`, `CenterView`, `RightView`
- Menggunakan `Provider` untuk manajemen state
- Mode pause dan restart game
- Namun sayangnya saat aplikasi dijalankan langsung menjalankan gamenya

---


---

## 🧠 Masalah yang Terjadi
Error:

Ini terjadi karena **`Board` membutuhkan `TickerProvider`**, tapi `TetrisView` adalah `StatelessWidget`.  
Solusinya adalah membuat widget pembungkus baru yang bersifat **Stateful**, agar bisa memberikan `TickerProvider`.
Banyak masalah yang terjadi saat saya mengimplementasikan perubahan pada saat saya menjalankan git clone
---
