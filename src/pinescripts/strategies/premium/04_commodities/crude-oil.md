# Crude Oil Strategy

The Crude Oil Strategy is designed to enter long or short positions based on a combination of specific price patterns observed over the last three days and a comparison of the current close with a historical close.

## Inputs

- **Lookback Period:** Defines the period over which the current close price is compared to the close price in the past to determine bullish or bearish conditions.

## Strategy Logic

### Conditions

- **Price Pattern Condition (cond1):**
  - Checks for specific price patterns over the last three days where each day's high is lower and low is higher than the previous day.

- **Bullish Condition (checkB):**
  - The current close price is greater than the close price `Lookback Period` days ago.

- **Bearish Condition (checkS):**
  - The current close price is less than the close price `Lookback Period` days ago.

### Long Position

- **Entry Condition:**
  - Enter a long position when both `cond1` and `checkB` are true.

### Short Position

- **Entry Condition:**
  - Enter a short position when both `cond1` and `checkS` are true.

## Execution

- **Enter Long:** When the long entry condition is met.
- **Enter Short:** When the short entry condition is met.

### Additional Notes
- **Position Size:** Set to 100% of equity, allowing for full allocation in trades.
