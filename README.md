# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Owlvans/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Owlvans/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,084 bytes of Python 3.13 (standard library only). `main.py` is an lzma-packed payload with a small unpacker; the source it unpacks to is a complete alpha-beta engine: its own legal move generation (castling, en passant, promotions), incremental Zobrist hashing and tapered piece-square scores, iterative deepening with PVS, a 2^20-entry transposition table, LMR and check extensions, quiescence (captures and promotions, all evasions in check), SEE capture ordering, and a tapered material + piece-square evaluation with a bishop-pair term. The search runs to a fixed budget of 80,000 nodes per move — no clock, no randomness — so every game replays move for move. It plays through the competition env (`MAKEFUN_ENV_URL`: POST /game, POST /move) and only ever plays moves from the env's legal-move list.

Local practice results with this exact file (kit trials, 6 games each against the house anchors): Elo 1654, 2112 (the scorer's cap, a 6-0 sweep) and 1191 — mean 1652 against the sunfish house baseline's mean of 1365, the prize gate. The same trial-2 opening set with colours flipped scored 1545, and a full 8-rung set scored 1530. Determinism was verified by re-running a trial and diffing all 470 plies.

## Run it

```sh
MAKEFUN_ENV_URL=<env server URL> python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=owl&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
