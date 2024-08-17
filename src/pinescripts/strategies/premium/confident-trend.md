# Confident Trend Strategy

This Pine Script strategy is designed to enter and exit long positions based on the relationship between a chosen symbol's price and its 200-day Simple Moving Average (SMA), combined with conditions related to the highest high and lowest low of the asset's price over a specified lookback period.

## Inputs

- **Comparative Symbol:** A symbol (e.g., SPY) used for comparison to guide entry and exit decisions.
- **Lookback Period for Highest High:** Defines the period over which the highest high is determined for entry conditions.
- **Lookback Period for Lowest Low:** Defines the period over which the lowest low is determined for exit conditions.

## Strategy Logic

### Entry Condition

- **Enter Long Position:**
  - The asset's closing price must be higher than the highest high of the past `Lookback Period for Highest High`.
  - The comparative symbol's (e.g., SPY) closing price must be above its 200-day SMA.

### Exit Condition

- **Close Long Position:**
  - The comparative symbol's closing price falls below its 200-day SMA.
  - OR the asset's closing price falls below the lowest low of the past `Lookback Period for Lowest Low`.

## Execution

- **Enter Long:** When the entry condition is met.
- **Exit Long:** When the exit condition is met.

### Additional Notes
- **Position Size:** Adjusted to 5% of the equity as per the strategy design.
