# Improved Index Trend Strategy

The Improved Index Trend Strategy is designed to capture market trends by entering and exiting long positions based on the relationship between fast and slow moving averages (MAs).

## Inputs

- **Fast Moving Average Length:** Defines the period for calculating the fast moving average, adjustable for backtesting.
- **Slow Moving Average Length:** Defines the period for calculating the slow moving average, adjustable for backtesting.

## Strategy Logic

### Moving Averages

- **Fast Moving Average:** Calculated using the user-defined fast MA length.
- **Slow Moving Average:** Calculated using the user-defined slow MA length.

### Trend Identification

- **Bullish Trend:** Occurs when the fast MA is above the slow MA.
- **Bearish Trend:** Occurs when the fast MA is below the slow MA.

### Long Position

- **Entry Condition:**
  - Enter a long position when a bullish trend is identified (fast MA is above slow MA).

- **Exit Condition:**
  - Close the long position when the trend turns bearish (fast MA falls below slow MA).

## Execution

- **Enter Long:** When the bullish trend condition is met.
- **Close Long:** When the bearish trend condition is met.

### Additional Notes
- **Position Size:** Set to 100% of equity, allowing for full allocation in trades.
