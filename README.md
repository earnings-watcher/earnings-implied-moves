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
