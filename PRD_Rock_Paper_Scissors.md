# Product Requirements Document: Rock Paper Scissors

## Summary

Create a standalone Rock Paper Scissors game that runs by opening one HTML file in a browser. A player competes against a computer opponent in a match; the first side to win three rounds wins the match.

## Background

The repository already contains a single-file, dependency-free browser game. This addition should follow that simple run-anywhere model while remaining a separate game that does not change the existing Memory Game.

## Problem and audience

People looking for a quick, familiar game need a simple way to play Rock Paper Scissors without installing software, creating an account, or setting up a server. The game is intended for casual play by children and adults.

## Goals

- Make a complete match playable in a desktop or mobile browser.
- Make the three choices immediately recognizable and easy to select.
- Clearly show both choices, the round outcome, match score, and ties.
- Keep interaction accessible to keyboard and assistive-technology users.
- Require no network connection, external dependencies, or persistent storage.

## Non-goals

- Online multiplayer, accounts, chat, or leaderboards.
- Difficulty settings, tournament brackets, or customizable rules.
- Saving match history or scores across page reloads.
- Editing or replacing the existing Memory Game.

## User stories

- As a player, I can choose rock, paper, or scissors and see the computer's choice and the round result.
- As a player, I can see the score and ties as the match progresses.
- As a player, I know when someone reaches three wins and can start a new match.
- As a keyboard or assistive-technology user, I can identify and activate each choice and receive a clear announcement of the result.

## Game rules and flow

1. A new match begins at 0-0 with no ties.
2. The player chooses rock, paper, or scissors. The computer chooses randomly from the same three options.
3. Rock beats scissors, scissors beats paper, and paper beats rock.
4. A tie increments the tie count but awards no match point.
5. The first side to reach three round wins ends the match. Choices are disabled until a new match is started.
6. Starting a new match clears the current score, tie count, choices, and result.

## Requirements

- Deliver the game as `rock-paper-scissors.html`, with HTML, CSS, and JavaScript in that file.
- Deliver this specification as `PRD_Rock_Paper_Scissors.md` in the same repository.
- Present three clearly labeled, keyboard-operable choice buttons.
- Display the player's selection and computer selection for each round.
- Display a human-readable outcome after each selection, including ties.
- Display player wins, computer wins, and tie count throughout the match.
- End a match as soon as either side reaches three wins; disable choice buttons and provide a New Match action.
- Make the result available through a polite live region and retain visible keyboard focus.
- Adapt the layout to narrow screens without horizontal overflow or overlapping text.
- Respect reduced-motion preferences for any nonessential animation.
- Use no external libraries, assets, requests, or storage. The file must work when opened directly from disk.

## Acceptance criteria

- Opening the HTML file starts a playable new match without setup or network access.
- Each of the three buttons produces a valid player choice and one computer choice.
- The outcome logic follows the standard rules; equal choices result in a tie and no point.
- Ties update only the tie count. Player and computer points update only on wins.
- Reaching three wins ends the match and prevents further choices until New Match is selected.
- New Match resets all match state and allows play again.
- Choice controls work with mouse, touch, and keyboard and have clear accessible names.
- Screen-reader users receive round outcomes through a live announcement.
- The layout remains usable at desktop and mobile widths, including visible focus indicators.
- The game remains self-contained and does not modify or depend on the Memory Game.

## Manual verification

1. Open `rock-paper-scissors.html` directly in a browser.
2. Select each move and verify both choices and the outcome appear.
3. Play through a match until either side wins three rounds; verify the game ends and choices disable.
4. Select New Match and confirm the score, ties, choices, and result reset.
5. Use only the keyboard to reach and operate the choices and New Match control.
6. Check at a narrow/mobile viewport for readable labels, usable buttons, visible focus, and no horizontal overflow.
7. Confirm the game still works with network access disabled.