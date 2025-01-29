# Counter Punch Strategy

The Counter Punch Strategy is designed to enter and exit long and short positions based on the Relative Strength Index (RSI) and price movements relative to specific moving averages. This strategy is optimized for both oversold and overbought market conditions.

## Inputs

- **RSI Period:** Defines the period used for calculating the RSI, adjustable for backtesting purposes.
- **Short-Term Moving Average (SMA) Period:** Defines the period for calculating the short-term SMA, also adjustable for backtesting.

## Strategy Logic

### Long Position

- **Entry Condition:**
  - The RSI value must be below 10.
  - The current close price must be above the 200-period SMA.

- **Exit Condition:**
  - The current close price exceeds the short-term SMA.

### Short Position

- **Entry Condition:**
  - The RSI value must be above 90.
  - The current close price must be below the 200-period SMA.

- **Exit Condition:**
  - The current close price falls below the short-term SMA.

## Execution

- **Enter Long:** When the long entry condition is met.
- **Exit Long:** When the long exit condition is met.
- **Enter Short:** When the short entry condition is met.
- **Exit Short:** When the short exit condition is met.

### Additional Notes
- **Position Size:** Set to 100% of equity, allowing for full allocation in trades.
