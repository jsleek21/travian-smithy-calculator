# Travian: Legends — Troops vs Smithy Upgrade Calculator

A small static tool for deciding whether it's more resource-efficient to **train more troops** or **upgrade your Smithy** one level, for any unit in any of the 7 tribes.

## Use it

Just open `index.html` in a browser — no build step, no server needed. Or enable **GitHub Pages** on this repo (Settings → Pages → Deploy from branch → `main` / root) and share the link with your clan.

## How it works

1. Pick your tribe and unit.
2. Pick the stat you care about (Attack, Defence, Scout Attack, or Scout Resist — only the stats that unit actually has are shown).
3. Enter your unit's **current Smithy level** and **how many troops you currently own**.
4. It compares:
   - **Cost per stat point to train 1 more troop** (fixed cost, same at any Smithy level)
   - **Cost per stat point to upgrade the Smithy one level** (this upgrade boosts *every* troop you already own, so it gets more efficient the bigger your stack is)

Whichever is cheaper per stat point wins.

## Data sources

- **Combat stats per level (1–20)**: Travian's official help center article, [More Troops or Smithy Upgrades?](https://support.travian.com/en/articles/186-more-troops-or-smithy-upgrades)
- **Smithy upgrade resource costs per level (1–20)**: [kirilloid.ru Travian troop calculator](http://travian.kirilloid.ru/troops.php), cross-checked against live in-game "Improve weapons and armor" screens on a real T4.5/T4.6 server — numbers matched exactly.
- **Base troop training costs**: same kirilloid dataset.

All data lives in `data.js` as a plain JS object — easy to update if Travian rebalances costs, or extend with more units.

## Known limitations

- Doesn't factor in **build time**, **crop upkeep over time**, or **Smithy building-level prerequisites** for reaching higher upgrade levels.
- Level-0 stat (pre-upgrade) is estimated by extrapolating backward from levels 1–2, since the source table starts at level 1. Fine for comparison purposes, not exact.
- Siege weapons (rams, catapults) and expansion units (settlers, chiefs) aren't included — this tool is for combat troop stat efficiency.

## Contributing

Numbers came from a third-party calculator + manual verification, not Travian's source code — if you spot something off vs. your own server, open an issue or just edit `data.js` directly.
