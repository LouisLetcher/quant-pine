# Lazy Trend Follower Strategy

The Lazy Trend Follower Strategy is a simple trend-following approach that enters and exits long positions based on the relationship between the closing price and a moving average (SMA).

## Inputs

- **Moving Average Length (M):** Defines the period for calculating the Simple Moving Average (SMA), adjustable through the Strategy Tester.

## Strategy Logic

### Moving Average Calculation

- **Simple Moving Average (SMA):** Calculated using the user-defined length `M` and based on the closing prices.

### Long Position

- **Entry Condition:**
  - Enter a long position when the closing price is greater than the SMA.

- **Exit Condition:**
  - Close the long position when the closing price falls below the SMA.

## Execution

- **Enter Long:** When the closing price is above the SMA.
- **Close Long:** When the closing price is below the SMA.

### Additional Notes
- **Position Size:** Set to 100% of equity, allowing for full allocation in trades.
