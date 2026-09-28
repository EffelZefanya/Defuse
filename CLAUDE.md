# Defuse — project notes for Claude Code

Co-op, pass-and-play card game (2–6 players) in a single self-contained `index.html`: vanilla HTML/CSS/JS, no framework, no build step. Open the file in a browser to run it. `README.md` has the player-facing rules.

## Code layout (all in index.html)

- `<style>`: design tokens on `:root`, then sections for hero/setup, cards, bombs, game HUD, overlays, guide page. Deliberately single dark theme.
- `<script>` (one IIFE):
  - Config constants: `COLORS`, `DIFF` (difficulty presets), `ROLES`, `ROLE_GUIDE`, `CARD_GUIDE`, `EVENT_GUIDE`, `TOGGLES`.
  - State: `setup` (setup-screen choices), `S` (the running game, `null` on the setup screen), `UI` (`sel` selected card id, `pending` role awaiting a bomb tap, `modal`).
  - Rendering: full re-render via `innerHTML` — `renderSetup()`, `renderGame()`, `overlayHTML()`, `openGuide()` (guide renders into a separate `#guide` element so game state is untouched).
  - Rules: `canPlay`, `playOnBomb`, `afterAction`, `endTurn`, `spawnBomb`, `flipEvent`, `useRole`, `useSelected`, `doSwap`, `discardSelected`.
  - Input: one delegated `click` listener switching on `data-act` attributes.

## Game rules as implemented

- Deck: numbers 1–9 × 4 colours × 2 copies (72). Action cards add 4 Wild, 3 Swap, 3 Freeze.
- A turn is one play (Engineer role gives two): play a card on a bomb, use a Swap/Freeze, or discard & draw. Roles don't use the play.
- Exact hit defuses; overshoot jams (total → 0, fuse −1) unless the Steady hands event is active (card bounces).
- After each turn every fuse drops by 1 unless the clock is frozen. A new bomb spawns every `spawn` turns while below `max`; each spawn flips an event when the Event deck is on.
- Bomb fuse = preset fuse + floor((target − tmin) / 3).
- Win at `goal` defuses; lose when any fuse hits 0.

## Design

Fonts from Google Fonts: Big Shoulders Stencil Display (display), Barlow (body), JetBrains Mono (fuse digits). Card colours are the `--red/--blue/--green/--yellow` tokens; each colour also has a symbol (◆ ● ▲ ■) for colour-blind players — keep both when adding UI. Amber `--haz` is the single accent (hazard tape, selection, buttons).

## Open ideas / known gaps

- Balance is untested; preset numbers in `DIFF` are first guesses.
- No "Hard" preset between Normal and Nightmare.
- Difficulty doesn't scale with player count.
- Possible additions: custom sliders for fuse/spawn/targets, Hanabi-style hint tokens for Silent mode, sound effects, saving settings in localStorage.
