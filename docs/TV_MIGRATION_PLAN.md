# quant-pine — TradingView Migration & Alignment Plan

Plan of record for aligning this repo with the quant-system strategy library and
the tv-quant-lab execution platform. Companion documents:

- `tv-quant-lab/docs/TRADINGVIEW_PORTABILITY.md` — classification of all 182
  quant-system Python strategy modules (≈111 are TradingView-portable).
- `tv-quant-lab/docs/BOOTSTRAP_PLAN.md` — nightly backtest farm + signal service.

quant-system is a **read-only research reference**: its Python modules are the
rule source when writing Pine ports, but nothing is committed there and nothing
here depends on its engine. All backtesting of Pine ports happens in the
TradingView Strategy Tester (driven via the TV MCP servers in tv-quant-lab).

## Role of this repo

quant-pine is the **public distribution channel** for Pine Script strategies:
free scripts under MIT, premium scripts marketed here (spec `.md`) but delivered
via Patreon/TradingView invite-only. It is **not** the execution platform —
webhook-driven execution, backtesting, and the signal service live in
tv-quant-lab. quant-system remains the research source of truth.

```
quant-system (Python research — read-only rule source)
     │  port (category A/B strategies)
     ▼
quant-pine (public funnel: free .pine MIT + premium specs)
     │  same code + alert payloads
     ▼
tv-quant-lab (private ops: manifests, TV Strategy Tester farm,
              webhook → Stripe/Telegram)
```

## Current state (2026-07)

- 4 implemented `.pine`: `conners-relative-strength-index` (v5 indicator),
  `bullish_engulfing`, `inside-days`, `stan-weinstein` (v6 strategies).
- 7 premium spec `.md`, **zero** premium implementations.
- No alerts/webhooks anywhere, no risk management (`strategy.exit`) anywhere,
  no Pine linting/CI, inconsistent naming (kebab vs snake), v5/v6 drift.
- Dormant since 2025-01; 15 of 20 asset-class folders empty.

### Content bugs to fix first

1. `strategies/premium/02_stocks/face_the_train.md` is a byte-identical copy of
   `lazy_trend_follower.md` — the real Face-the-Train rules (contrarian entry
   after 3 consecutive down days above the 200 SMA, per
   `quant-system/strategies/signals/python/face_the_train.py`) are missing.
2. Two conflicting "Lazy Trend Follower" specs (`02_stocks` vs `09_etfs`) with
   different rule sets. Keep one canonical spec (the `02_stocks` variant, which
   matches the Python implementation) and make the ETF page reference it.
3. `trend-risk-protection.md` CTA references the wrong strategy ("Linear
   Regression Strategy").
4. `.github/workflows/stale.yml` still ships placeholder messages.

## Alignment decisions

| Topic | Decision |
|---|---|
| Pine version | v6 everywhere; upgrade `conners-relative-strength-index.pine` from v5 |
| Naming | `snake_case.pine`, matching quant-system module names 1:1 (e.g. `counter_punsh.py` → `counter_punsh.pine`); rename `inside-days.pine` → `inside_day.pine`, `stan-weinstein.pine` → `stan_weinstein.pine` |
| Declaration | Keep `"<AssetClass> - <Name>"` title convention, `default_qty_type=strategy.percent_of_equity, default_qty_value=100` |
| Risk management | Every new strategy ports the Python exits faithfully (`strategy.exit` with stops/targets where the Python version has them; no silent all-in-long-only simplification) |
| Alerts | Every free strategy ships `alertcondition()` with the JSON payload from `tv-quant-lab/config/alert_schema.json`: `{action, symbol, signal, price, bar_time, timeframe, confidence}` — this is the contract the webhook gateway already parses |
| Licensing | Premium `.pine` source is **never committed here** (public repo). Premium implementations live in tv-quant-lab (private); this repo keeps the marketing `.md` spec only |
| Lint/CI | Add `[*.pine]` to `.editorconfig`; add a CI job validating: `//@version=6` header, `alertcondition` present in every free strategy, filename convention |
| README | Add the per-script index that CONTRIBUTING already promises |

### Standard file template

```pine
//@version=6
strategy("Stocks - Counter Punch", shorttitle = "Stocks - Counter Punch",
     overlay=true, default_qty_type = strategy.percent_of_equity, default_qty_value = 100)

//-------------------------------------------
// User Inputs
//-------------------------------------------
rsiLength = input.int(2, title="RSI Length", minval=1)
...

//-------------------------------------------
// Conditions
//-------------------------------------------
...

//-------------------------------------------
// Orders
//-------------------------------------------
if longEntryCondition
    strategy.entry("Long", strategy.long)
if longExitCondition
    strategy.close("Long")

//-------------------------------------------
// Alerts (webhook contract: tv-quant-lab alert_schema.json)
//-------------------------------------------
alertcondition(longEntryCondition, title="Long Entry",
     message='{"action":"buy","symbol":"{{ticker}}","signal":1,"price":{{close}},"bar_time":"{{time}}","timeframe":"{{interval}}","confidence":1.0}')
alertcondition(longExitCondition, title="Long Exit",
     message='{"action":"close","symbol":"{{ticker}}","signal":0,"price":{{close}},"bar_time":"{{time}}","timeframe":"{{interval}}","confidence":1.0}')
```

## Migration waves

### Wave 0 — hygiene (½ day)
- Fix the four content bugs above; add editorconfig rule, CI lint, README index.
- Upgrade the Connors RSI indicator to v6; retrofit alerts onto the 3 existing
  free strategies.

### Wave 1 — free tier: the validated round-trips (≈15 scripts, ~1 week)
Strategies that originated in Pine and were validated in quant-system's daily
backtest — porting back is mechanical. Target folders in parentheses:

`rsi`, `macd`, `mfi`, `adx`, `bollinger_bands`, `donchian_channels_breakout`,
`larry_williams`, `pullback`, `weekly_breakout`, `turtle_trading` (02_stocks);
`bitcoin` (05_crypto); `crude_oil` (04_commodities); `inside_day`,
`bullish_engulfing` (already present, add alerts); `lazy_trend_follower`
(01_all_markets, free teaser variant).

This restores the free catalog that commit `8c9cc0c` deleted, now with alerts,
proper exits, and a Python twin in quant-system for every script.

### Wave 2 — premium specs get real implementations (in tv-quant-lab)
`counter_punsh`, `improved_index_trend`, `trend_risk_protection`,
`linear_regression`, `face_the_train` (correct rules), `lazy_trend_follower`
(full variant). Specs here get a parameter table + backtest summary sourced from
the nightly farm; `.pine` source goes to tv-quant-lab only.

### Wave 3 — premium catalog expansion (from portability doc, ongoing)
High-conviction category-A families, one spec page per strategy, filling the
empty asset-class folders:

- 02_stocks: turtle systems 1&2, VCP family, O'Neil pair, gap family
- 03_indices: regime-filtered trend family
- 04_commodities: vol-targeted commodity trend, commodity seasonality
- 05_crypto: ATR vol-target, breakout-retest, regime-filtered crypto trend
- 07/08_bonds: vol-targeted treasury/corporate/TIPS/muni + curve strategies
  (category B, `request.security` on TVC yields)
- 09_etfs: defensive/cyclical timing, credit-spread strategies

Category C strategies (cross-sectional, pairs, curve panels — ~41 modules) are
**out of scope** for TradingView and stay Python-only in quant-system.

## Definition of done per script

1. `.pine` compiles clean on TradingView (v6, no warnings).
2. Alert payloads validate against `alert_schema.json`.
3. Strategy Tester run on the manifest symbol/timeframe is the authoritative
   validation (results captured into the tv-quant-lab farm via the TV Desktop
   MCP). Sanity parity vs the quant-system Python rules: same entry/exit logic
   by inspection, same sign of total return over a shared window.
4. Listed in README index; manifest added/updated in tv-quant-lab.
