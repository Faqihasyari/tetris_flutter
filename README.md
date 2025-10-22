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

---


---

## 🧠 Masalah yang Terjadi
Error:

Ini terjadi karena **`Board` membutuhkan `TickerProvider`**, tapi `TetrisView` adalah `StatelessWidget`.  
Solusinya adalah membuat widget pembungkus baru yang bersifat **Stateful**, agar bisa memberikan `TickerProvider`.

---

## ✅ Solusi Implementasi

### `game_screen.dart`
```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

import 'board.dart';
import 'tetris_view.dart';

class GameScreen extends StatefulWidget {
  const GameScreen({super.key});

  @override
  State<GameScreen> createState() => _GameScreenState();
}

class _GameScreenState extends State<GameScreen> with TickerProviderStateMixin {
  late final Board board;

  @override
  void initState() {
    super.initState();
    board = Board(this); // memberikan TickerProvider
  }

  @override
  void dispose() {
    board.dispose(); // penting untuk menghindari memory leak
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return ChangeNotifierProvider.value(
      value: board,
      child: const TetrisView(),
    );
  }
}
