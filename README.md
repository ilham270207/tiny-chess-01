# TinyKnight

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ilham270207/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ilham270207/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

**TinyKnight** — a chess engine in under 4 KB of Python, built for the [tiny-chess-01](https://make.fun/bounty/tiny-chess-01) bounty. 0x88 board, alpha-beta search with iterative deepening to a fixed node budget, quiescence search, transposition table, null-move pruning and check extensions. It talks to the make.fun env over HTTP and also speaks UCI for local testing.

## Run it

```sh
python3 main.py
# UCI: uci, isready, position startpos, go depth 3
```

Set `MAKEFUN_ENV_URL` to play the env trials instead.

## Desain TinyKnight

TinyKnight adalah engine catur yang ditulis dari nol dengan papan 0x88
dan piece-list plus Zobrist transposition table (seed deterministik).
Pencarian memakai alpha-beta dengan iterative deepening sampai budget
tetap 200.000 node per langkah (tanpa jam — deterministik), quiescence
search (capture + penghindaran skak + delta pruning), ordering
MVV-LVA + killer + history, koreksi mate per-ply di TT, dan
null-move pruning dengan check extension. Evaluasi: material +
piece-square table prosedural (dihitung saat startup dari rumus
sendiri) + sentralisasi raja di endgame. Semua langkah legal lengkap:
castling, en passant, promosi, skak/mat/stalemate, plus penjaga
repetisi.

## Cara menjalankan & menguji

Engine berbicara protokol UCI. Jalankan `python3 main.py`, lalu kirim:
`uci`, `isready`, `position startpos`, `go depth 3` — engine menjawab
`bestmove` yang legal (contoh: `bestmove b1c3`).

Untuk kebenaran move generator, jalankan perft dari posisi awal:
kedalaman 3 harus 8.902 node, kedalaman 4 harus 197.281 node; posisi
Kiwipete kedalaman 3 harus 97.862 node.

Untuk uji tanding lokal, jalankan server env dari kit dengan node,
set `MAKEFUN_ENV_URL` ke alamat server, lalu mainkan via
`POST /game` dan `POST /move` (batas 10 detik per langkah).
