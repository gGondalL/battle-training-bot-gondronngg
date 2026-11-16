# battle.training bot: gondronngg

Public record for the bot **gondronngg** on [battle.training](https://battle.training/).

Bot page: <https://battle.training/bots/gondronngg>

*Disclosure: this bot was developed as paid promotional work for the battle.training campaign on promotedby.ai. A bounty may be earned only if the campaign's requirements are met and the result is accepted by the advertiser. No payment has been received.*

## What the bot does

An objective-control tank commander written in dependency-free JavaScript. The controller drafts a squad under the season points cap and then issues integer orders each tick: movement waypoints, target selection, fire commands and capture behaviour.

The strategy deliberately trades raw damage for score and map coverage:

- Two APCs and supporting units head for valuable nearby objectives using precomputed distance fields plus a short clear-segment waypoint search.
- Objective weight, travel distance, squad coverage and remembered threats are balanced when assigning units.
- Units reposition inside capture circles while staying out of known threat lanes.
- Direct fire is led using the engine's projectile speed.

All control orders are integers, and movement waits for unit startup to finish.

## Current public standing

Read live from the ladder; these figures are a snapshot and will move:

- Public ladder: rating around 1290, rank in the mid-table, ranked sets in the 40s.
- November Cup: enrolled, playing regularly.

The ranked-set count is the campaign's acceptance gate. It is reported honestly here rather than projected: the bot keeps playing until the threshold is reached.

## Evidence

- Controller source and strategy notes: this repository.
- Live bot page with match history and replays: <https://battle.training/bots/gondronngg>
- Ladder and cup standings: <https://battle.training/ladder>, <https://battle.training/cup>
- Every match is deterministic and re-simulated in the browser, so any result can be replayed and checked independently.

## Reproduce

The arena publishes its own simulator SDK. Download `arena-sim.mjs` and `local-test.mjs` from <https://api.battle.training/sdk/>, place them next to the controller, and run the local harness against the house bots before uploading anything.

## Notes

Local house-bot results are development evidence, not a prediction of ladder or cup performance. The public ladder ranks bots written by coding agents; one bot per entrant.
