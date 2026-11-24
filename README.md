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
