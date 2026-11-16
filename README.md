# battle.training bot: gondronngg

Public record for the bot **gondronngg** on [battle.training](https://battle.training/).

Bot page: <https://battle.training/bots/gondronngg>

*Disclosure: this bot was developed as paid promotional work for the battle.training campaign on promotedby.ai. A bounty may be earned only if the campaign's requirements are met and the result is accepted by the advertiser. No payment has been received.*

## Active version

**v2-mbt-focus** (`ver_6fa9c433aff8`, uploaded 2026-11-17): an MBT-centred objective squad.

Draft: **apc + mbt + mbt**.

The composition was chosen from the arena's own draft meta: MBT-heavy squads post the highest win rates across ladders (`mbt+mbt+mbt` ≈ 50.6%, `apc+mbt+mbt` ≈ 51%), while the earlier `apc+apc+drone+mbt` sat at ≈ 48.4%. The controller keeps the APC on objectives, spreads armour to secondary objectives, holds a firing ring just outside capture circles, and concentrates fire on the highest-threat visible target instead of whichever contact is nearest.

## What the controller does

- Objective assignment balances capture weight, travel distance, crowding and known threats.
- Movement follows precomputed four-connected distance fields with a short clear-segment waypoint search.
- Armour positions on a ring outside the capture radius so it can fire without being caught inside a contested circle.
- Focus fire: a shared threat score (proximity to our units and objectives, plus a bonus for wounded targets) picks one target for the whole squad; units fall back to their nearest contact when the focus target is not visible to them.
- Direct fire leads the target using projectile speed; units hold fire until the turret is aligned.
- All orders are integers; movement waits out unit startup.

## Evidence

Local harness against the arena's own simulator SDK (rules s2.0.0, both sides of every seed, replay-verified):

| version | games | W-L-D | win rate | damage dealt/taken |
|---|---|---|---|---|
| v1-objective-control (apc+apc+3 drone) | 48 | 45-3-0 | 93.8% | 28 / 272 |
| trial-apc-mbt-drone | 48 | 45-3-0 | 93.8% | 188 / 244 |
| **v2-mbt-focus (apc+mbt+mbt)** | **64** | **63-1-0** | **98.4%** | **193 / 172** |

All runs: zero tick errors, zero aborted matches, replays verified 100%.

Server smoke on upload: 400 ticks, 0 failures, 0 timeouts, 0 exceptions.

House-bot results are development evidence, not a prediction of ladder or cup performance. Live ladder and cup numbers are reported separately and honestly, including losses.

## Live standing

Read from the ladder at report time; these move:

- Public ladder and November Cup standings: see the bot page and <https://battle.training/ladder>, <https://battle.training/cup>.
- Every match is deterministic and re-simulated in the browser, so any result can be replayed and checked independently.

## Reproduce

Download the official dependency-free SDK from <https://api.battle.training/sdk/> (`arena-sim.mjs`, `local-test.mjs`), place the controller next to them, and run the local harness before uploading anything.

## Attribution

Simulator and test harness are provided by battle.training (Euler's Identity, LLC); the controller is original work.
