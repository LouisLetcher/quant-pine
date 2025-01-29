# Stable Mean Revert Strategy

The Stable Mean Revert Strategy aims to capitalize on mean-reversion opportunities by entering long positions when the market is oversold, as indicated by the RSI, and the broader market (represented by SPY) is in a bullish condition. The strategy uses a simple exit condition to lock in profits.

## Inputs

- **Comparative Symbol:** Defines the symbol (e.g., SPY) used for comparison to guide entry and exit decisions.
- **RSI Period:** Defines the period for calculating the Relative Strength Index (RSI), adjustable for backtesting.

## Strategy Logic

### Moving Averages

- **200-Day SMA (for Comparative Symbol):** Calculated for the comparative symbol (e.g., SPY) to determine the broader market trend.

### RSI Calculation

- **RSI:** Calculated using the user-defined period to identify oversold conditions.

### Long Position

- **Entry Condition:**
  - Enter a long position when the RSI is below 30, indicating an oversold condition.
  - The comparative symbol (e.g., SPY) must be above its 200-day SMA, indicating a bullish market condition.

- **Exit Condition:**
  - Close the long position when the current closing price is greater than the previous day's closing price, signaling a potential recovery.

## Execution

- **Enter Long:** When the entry conditions are met (RSI < 30 and SPY > 200-day SMA).
- **Close Long:** When the exit condition is met (closing price > previous day's close).

### Additional Notes
- **Position Size:** Set to 5% of equity to manage risk effectively.
