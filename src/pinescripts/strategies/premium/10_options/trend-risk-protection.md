# Trend Risk Protection Strategy

The Trend Risk Protection Strategy is a trend-following strategy that aims to capture uptrends and protect against downtrends by entering and exiting long positions based on the relationship between the closing price and a 200-period Simple Moving Average (SMA).

## Strategy Logic

### Moving Average Calculation

- **200-Period SMA:** Calculated using the closing price over a 200-period window. This SMA acts as a key indicator of the overall trend.

### Position Conditions

- **Long Condition:**
  - A **crossover** occurs when the closing price moves above the 200-period SMA, indicating the beginning of an uptrend.
  - The strategy confirms this by ensuring the current close is above the SMA, signaling a strong bullish trend.

- **Sell Condition:**
  - A **crossunder** occurs when the closing price falls below the 200-period SMA, indicating a potential downtrend.
  - The strategy confirms this by ensuring the current close is below the SMA, signaling a strong bearish trend.

### Long Position

- **Entry Condition:**
  - Enter a long position when the closing price crosses above the 200-period SMA and remains above it.

- **Exit Condition:**
  - Close the long position when the closing price crosses below the 200-period SMA and remains below it.

## Execution

- **Enter Long:** When the long condition is met (crossover and close > SMA).
- **Close Long:** When the sell condition is met (crossunder and close < SMA).

### Additional Notes
- **Position Size:** Set to 100% of equity, allowing for full allocation in trades.
