# Product Context: Memory Game

## Product summary

This repository contains a responsive, browser-based memory matching game. The player reveals cards, remembers their symbols, and finds matching pairs on a 4x4 or 6x6 board. The game is implemented as a standalone HTML file with embedded CSS and JavaScript and has no external dependencies.

The repository name is `memory-game-GHCP`. The README and source do not define what `GHCP` stands for.

## Four-part game flow

1. **Choose a board:** Start with the 4x4 grid or select the 6x6 grid.
2. **Reveal cards:** Select cards with a mouse, touch, or keyboard to reveal their symbols.
3. **Find pairs:** Match all pairs. The game tracks moves, elapsed time, and a star rating; unmatched cards flip back after a short delay.
4. **Finish and replay:** When every pair is matched, view the completion summary and start another game with Play Again.

## Features in the current implementation

- 4x4 and 6x6 board sizes.
- Animated card flips and matching feedback.
- Move counter, timer, and move-based star rating.
- Best-score list saved locally in the browser, limited to five scores.
- Keyboard card interaction and visible focus styling.
- Responsive layout for smaller screens.
- Light and dark themes, with light mode as the default when no theme preference is saved.
- Theme preference saved separately from scores; game play remains available if browser storage is unavailable.

## Technical scope

- Main application: `memory-game.html`.
- Technologies: HTML, CSS, and JavaScript in a single file.
- No backend, accounts, network services, or external runtime libraries are present.
- Game scores use the browser storage key `memoryGameScores`.
- Theme preference uses the separate browser storage key `memoryGameTheme`.

## Boundaries

This is a local browser game, not a multiplayer service. The source does not establish user accounts, online leaderboards, cloud score synchronization, or a meaning for the `GHCP` suffix in the repository name.