# Defuse

A co-op card game for 2–6 players, played pass-and-play on one screen. Bombs land on the table, each with a colour and a target number. Play matching cards to hit each target exactly before its fuse burns out. Defuse enough bombs together and the whole team wins.

## Play

Open `index.html` in a browser. There's no build step and nothing to install.

## How a turn works

1. Pick a card from your hand, then tap a bomb of the same colour. The card's number adds to that bomb's total.
2. Hit the target exactly and the bomb is defused. Go over and it jams: the total drops back to 0 and the fuse loses 1.
3. No good play? Discard a card to draw a new one. That uses your turn.
4. After every turn the clock ticks and every fuse drops by 1. New bombs arrive every few turns.

The team wins by defusing the goal number of bombs. If any fuse reaches 0, everyone loses.

## Difficulty

| | Easy | Normal | Nightmare |
|---|---|---|---|
| Bombs to defuse | 6 | 8 | 10 |
| Starting fuse | 14 | 12 | 10 |
| New bomb every | 5 turns | 4 turns | 3 turns |
| Target range | 8–14 | 10–17 | 12–20 |
| Cards in hand | 5 | 5 | 4 |
| Max bombs on table | 4 | 4 | 5 |

Bigger targets burn longer: a bomb gets +1 fuse for every 3 points its target sits above the lowest target in the range. On Normal, a target-10 bomb starts at 12 and a target-17 bomb starts at 14.

## Modifiers

- **Action cards**: Wild (any bomb, you pick 1–6), Swap (trade a card with a teammate), Freeze (stop the clock for 2 ticks).
- **Roles**: one power per player, usable once per game: Engineer, Cooler, Tinker, Recycler, Surgeon, Clockmaker.
- **Event deck**: a twist flips each time a new bomb lands (Lockdown, Shaky hands, Steady hands, Aftershock, Calm, Adrenaline, Quiet shift).
- **Hidden hands**: only the current player sees their cards; a pass screen appears between turns.
- **Silent mode**: a table rule, no saying the colours or numbers in your hand.

The in-game **Roles & cards** page explains every role, action card and event.
