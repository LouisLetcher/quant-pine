# NR7 Strategy

The NR7 Strategy focuses on identifying periods of compression in price volatility, known as NR7 days. An NR7 day is one where the trading range (high minus low) is the narrowest of the last seven days (the current day plus the previous six days). The idea is that periods of low volatility often precede explosive moves. By identifying these narrow-range days, traders may attempt to position themselves for potential breakouts.

## Inputs & Calculations

- **Range Calculation:**
  - **Today’s Range:** The difference between today's high and low.
  - **Past 6 Days’ Lowest Range:** The smallest daily range observed in the previous six trading sessions.

- **NR7 Condition:**
  - The strategy checks if today’s range is smaller than all of the previous six days’ ranges.
  - If `todayRange < lowestRangePast6`, it flags the day as an NR7 day.

## Strategy Logic

1. **Identify NR7 Day:**
   - If the current day’s range is the narrowest in the last seven days, the strategy considers this a low-volatility compression period potentially primed for a breakout.

2. **Entry Condition:**
   - On NR7 days, the strategy enters a long position at the close of the bar if no current position is held.
   - This anticipates a possible breakout from the narrow range on subsequent days.

3. **Exit Condition:**
   - The strategy exits the long position when today’s close exceeds yesterday’s high.
   - This suggests that the price has broken out to the upside, and the strategy locks in profits.

## Execution Flow

1. **Check Volatility Compression:**
   Determine if today’s range is the smallest over the last seven days.

2. **Enter Long on NR7:**
   If true and not currently in a position, enter long at the close of today’s bar.

3. **Exit on Breakout Confirmation:**
   On subsequent days, if the close surpasses the previous day’s high, close the position to capture profits.

## Additional Notes

- **Position Sizing:**
  The strategy uses 100% of equity for each trade, which can be risky. Adjust this to fit your risk tolerance and trading plan.

- **Timeframe and Markets:**
  This strategy works best in markets or timeframes where the NR7 pattern is a reliable indicator of upcoming volatility expansions. Be sure to test and validate before using it in live trading.
