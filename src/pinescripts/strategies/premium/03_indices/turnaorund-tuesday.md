# Turnaround Tuesday Strategy

The Turnaround Tuesday Strategy is based on a simple pattern observed in daily price movements, particularly in equity markets like the S&P 500 (represented by SPY). It aims to exploit a common phenomenon where a Monday decline is followed by a bounce on Tuesday.

## Timeframe & Markets

- **Timeframe:** Daily charts.
- **Symbol Example:** SPY (S&P 500 ETF).
- **Assumption:** The behavior is that if the market experiences a down-close on Monday, there may be a rebound on Tuesday.

## Strategy Logic

1. **Identify Monday and Tuesday:**
   - **Monday Check:** If today is Monday and today’s close is lower than the previous day’s close (which would be Friday since weekends are non-trading days), the strategy considers this a potential "turnaround" setup.

2. **Entry Condition (On Monday):**
   - If the Monday close is below the Friday close, the strategy enters a long position at Monday’s close.

3. **Exit Condition (On Tuesday):**
   - If a position is currently held, the strategy exits at Tuesday’s close. The idea is to capture a potential rebound that often occurs on Tuesday following a weak Monday.

## Execution Flow

1. **Monday Down Day:**
   Check if today (Monday) closed lower than yesterday (Friday).

2. **Enter Long at Monday’s Close:**
   If the condition is met, open a long position.

3. **Exit at Tuesday’s Close:**
   On the next trading day (Tuesday), if there’s an open position, close it at the day’s close.

## Additional Notes

- **Position Sizing:**
  The strategy uses 100% of equity for each trade by default. Adjust the position sizing according to your risk management preferences.

- **Testing & Validation:**
  Historical testing is recommended, as market behavior can change and the pattern may not persist indefinitely. Use the strategy as a starting point and adapt parameters or add filters to improve reliability.
