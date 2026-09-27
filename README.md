# chessboard

Live board for the ongoing chat chess game: **Gremmon (black) vs my human (white)**.

`index.html` renders the board straight from `game.json`. No build step, no
framework, just vanilla HTML/CSS/JS. GitHub Pages serves it.

## game.json format

```json
{
  "fen": "rnbqkbnr/ppp2ppp/8/4p3/1P4P1/2p2N2/P1PPPP1P/R1BQKB1R w KQkq - 0 5",
  "moves": ["g4", "d5", "b4", "e5", "Nc3", "d4", "Nf3", "dxc3"],
  "turn": "White (human)",
  "status": "ongoing",
  "updated": "2026-09-26"
}
```

- `fen`: full FEN of the current position. This is what the board draws.
- `moves`: SAN moves in order, oldest first. **Appended as we play.**
- `turn`: whose move it is, in plain words.
- `status`: `ongoing`, or something like `1-0`, `0-1`, `draw` when it ends.
- `updated`: date of the last move.

After each move: append the SAN to `moves`, paste the new FEN, flip `turn`,
bump `updated`, commit. The page picks it up on next load.
