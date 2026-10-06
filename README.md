# Earnings implied moves vs actual moves — EarningsWatcher open dataset

**3,393 earnings reports · 210 US stocks · 2021-03-31 to 2026-09-24 · updated 2026-10-06**

For every report: the move the options market priced in before the release (the *implied move*, from the
at-the-money straddle at the last close before the report), the stock's close-to-close move on the reaction
day, its peak intraday move, and whether the peak beat the implied. Across this dataset the actual peak
move exceeded the implied move in **54%** of reports.

Source: [EarningsWatcher](https://earnings-watcher.com) — the same figures published on each stock's page,
e.g. https://earnings-watcher.com/wiki/jpm-implied-move, and in the free JSON API
(`https://earnings-watcher.com/api/implied/JPM.json`). Methodology:
https://earnings-watcher.com/wiki/methodology · how the implied move is calculated:
https://earnings-watcher.com/wiki/how-to-calculate-implied-move

## What is free here, and what members get

This file is the free part of EarningsWatcher: for every report, what the options market priced in and what the stock then did. It is enough to study a stock's record or test an idea of your own. Everything below is what we built on top of it for the trade you have not placed yet.

**Before the report**
- **Live implied moves and the full earnings calendar** — every reporting stock, refreshed daily as options reprice, with ten years of implied-vs-actual history behind each name.
- **IV Rush Radar** — how a stock's option prices typically climb into its print, and where they stand today against that pattern, hour by hour on the last day.
- **Scanner and alerts** — screen every upcoming report by implied move, beat rate, liquidity or IV, and get told when a setup appears.
- **Moves Analyser** — the distribution of a stock's past earnings moves, not just the average, so a position can be judged on probabilities.

**Choosing the position**
- **Simulator** — the exact straddle, strangle, condor or spread you have in mind, priced against ten years of that stock's real reactions before you place it.
- **Backtester** — the same position run through every past report with real option prices, entry and exit.
- **Sympathy plays** — the stocks that move when a related company reports, measured over years of releases.

**After the report**
- **DriftLab** — whether the earnings-day move tends to continue or fade over the following weeks, scored from every past release.
- **Paper trading, journal and a live trade feed** — rehearse positions with no money at risk, keep notes, and see what other members are putting on.

**Around it**
- **The MCP connector** — the whole platform inside ChatGPT, Claude or Cursor: ask for the implied move, the radar reading or a simulated position in plain language.
- **API access**, daily livestreams, a private Discord, and a 15-lesson options course for anyone starting out.

Plans and prices: https://earnings-watcher.com/pricing — cancel anytime.

## Columns

| column | meaning |
|---|---|
| `symbol` | US ticker |
| `company` | company name |
| `report_date` | earnings release date (the date the report was published; for after-close reports the reaction day is the next session) |
| `implied_move_pct` | options-implied move, ± percent, at the last close before the report |
| `close_move_pct` | close-to-close move on the reaction day, percent, signed |
| `peak_move_pct` | largest intraday move on the reaction day vs the pre-report close, percent, signed |
| `beat_implied` | 1 if \|peak_move_pct\| ≥ implied_move_pct, else 0 (blank when the peak is not recorded) |

## Licence and attribution

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You may use, share and build on this data,
including commercially, provided you credit **EarningsWatcher** with a link to https://earnings-watcher.com.
Suggested citation: *EarningsWatcher, "Earnings implied moves vs actual moves" dataset, 2026-10-06,
https://earnings-watcher.com.* Education only — not investment advice.

## Python

```python
pip install git+https://github.com/earnings-watcher/earningswatcher-python
from earningswatcher import implied_move
implied_move("JPM")   # live implied move, next report date and the full history for one stock
# package: https://github.com/earnings-watcher/earningswatcher-python
```

## What is not here

Live implied moves into upcoming reports, IV rush readings, post-earnings drift scores, the simulator and
the straddle backtests are part of the EarningsWatcher membership: https://earnings-watcher.com/pricing
