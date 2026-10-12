# Product Requirements Document: Dark Theme

## Summary

Add an optional dark theme to the Memory Game in `memory-game.html`. Players can switch between the existing light appearance and a dark appearance without changing game rules, scores, or accessibility behavior. The selected theme persists across page reloads.

## Background

The project is a standalone, responsive memory matching game implemented in one HTML file with embedded CSS and JavaScript. It offers 4x4 and 6x6 boards, card-flip animations, move and time tracking, a star rating, keyboard controls, and locally stored best scores. The current interface uses a light background with blue card backs and controls.

This feature is a visual preference only. It must not alter the game flow or score data.

## Problem

Players who prefer a darker interface, or who play in low-light environments, currently have no alternative to the light theme. A dark theme should improve comfort while keeping cards, controls, statistics, and game feedback easy to distinguish.

## Goals

- Let players switch between light and dark themes at any time.
- Remember the selected theme after reloads and new games.
- Keep text and interactive elements legible and distinguishable in both themes.
- Preserve all existing game behavior and score history.
- Keep the game dependency-free and usable on desktop and mobile.

## Non-goals

- Redesigning the game or changing its layout, rules, scoring, or animations.
- Adding additional themes, custom color selection, accounts, or cross-device sync.
- Changing the `memoryGameScores` storage format or score-ranking behavior.
- Adding a framework, external package, or separate build process.

## Users and user stories

- As a player, I can switch to dark theme while playing so the interface is more comfortable in a dim environment.
- As a returning player, I see my previously selected theme when I reopen the game.
- As a keyboard or assistive-technology user, I can find, operate, and understand the theme control.
- As a player, I can still recognize card backs, revealed symbols, matches, focus, and completion feedback in either theme.

## Product requirements

### Theme control

1. Add a clearly labeled theme toggle near the existing game controls, without obscuring or displacing the board on narrow screens.
2. The control must be operable by mouse, touch, and keyboard. It must expose an accessible name and communicate the current theme and/or the action that will occur when activated.
3. The control switches immediately between light and dark themes without resetting the grid, timer, moves, rating, matched cards, or modal state.
4. On a first visit with no saved preference, use the existing light theme to preserve current behavior.

### Theme appearance

1. Dark theme must provide coordinated colors for the page background, primary text, controls, game cards, best-score area, and win modal and its backdrop.
2. Maintain clear contrast between card front and back, card symbols and their surface, buttons and their labels, and focused controls and surrounding content.
3. Preserve visible hover, active, focus, and matched states in both themes. Do not rely on color alone to indicate a match or focus.
4. Keep the current responsive layout and card-flip behavior. Theme changes must not cause layout shifts that interfere with card selection.
5. Respect readable contrast, targeting WCAG 2.2 AA contrast ratios for text and meaningful UI boundaries where applicable.

### Preference persistence

1. Store the theme preference separately from the existing `memoryGameScores` value.
2. Restore a valid saved preference on page load. If the stored value is absent or invalid, use light theme.
3. A storage read/write failure must not prevent the game from initializing or being played; use an in-memory theme for the current page session as a fallback.
4. Changing theme must not modify, clear, or reorder saved scores.

## Technical constraints

- Implement the feature in the existing `memory-game.html` file using its embedded CSS and JavaScript.
- Reuse CSS custom properties or an equivalent centralized theme mechanism so colors are not duplicated across unrelated selectors.
- Keep the existing score storage key, score data structure, matching logic, timer, grid-size controls, and keyboard card controls unchanged.
- Do not add external dependencies or require a server; the game must remain playable by opening the HTML file directly.

## Acceptance criteria

- A first-time player sees the existing light theme and can locate the theme control.
- Activating the control changes the full game interface to dark theme and activating it again returns to light theme.
- The selected theme remains after a page reload.
- Starting a new game, switching grid size, completing a game, or using Play Again does not unexpectedly change the selected theme.
- Theme switching during a game does not reset or change moves, elapsed time, rating, revealed cards, or matches.
- Previously saved scores remain visible and unchanged after switching themes and reloading.
- The theme control and all existing game controls remain keyboard accessible with visible focus indicators.
- Card faces, card backs, matched cards, statistics, buttons, best scores, and the completion modal are readable in both themes at desktop and mobile widths.
- If browser storage is unavailable, the page still loads and the game remains playable.
- No external requests or new runtime dependencies are introduced.

## Manual verification plan

1. Open `memory-game.html` directly in a browser and confirm the initial appearance matches the current light theme.
2. Switch themes before starting; confirm all visible surfaces update and the control reports the new state.
3. Start a game, reveal cards, and switch themes. Confirm the board, timer, moves, rating, and card states are preserved.
4. Switch between 4x4 and 6x6 and use Play Again; confirm the selected theme remains active.
5. Complete a game in each theme and inspect the modal and best-scores section.
6. Reload after selecting dark theme; confirm the selection persists and saved scores remain intact.
7. Use only the keyboard to reach and activate the theme control and play cards; confirm focus remains visible.
8. Check a narrow/mobile viewport for readable content, usable controls, and an unobstructed board.
9. Where practical, test with browser storage disabled or unavailable; confirm the game still initializes and can be played.

## Risks and mitigations

- **Insufficient contrast in dark surfaces:** define colors centrally and verify text, controls, cards, focus, and overlays in both themes.
- **Theme preference collides with scores:** use an independent storage key and verify existing scores before and after theme changes.
- **Theme switching disrupts a game:** limit switching to presentation state and explicitly test with active timers and revealed cards.
- **Storage is unavailable:** handle storage failures without blocking game initialization.

## Success criteria

The feature is ready when all acceptance criteria pass, the existing game remains playable in both themes, and saved score behavior is unchanged.