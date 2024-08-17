# Ride The Aggression Strategy

The Ride The Aggression Strategy is designed to capitalize on aggressive market movements by entering long positions based on Bollinger Bands and a comparative symbol's price behavior. The strategy also employs a dynamic trailing stop to manage risk.

## Inputs

- **Comparative Symbol:** Defines the symbol (e.g., SPY) used for comparison to guide entry and exit decisions.
- **Trailing Stop Percentage:** Specifies the percentage below the highest price to set the trailing stop.
- **Bollinger Bands Parameters:**
  - **Length:** Defines the period for the SMA used in Bollinger Bands calculation.
  - **Multiplier:** Defines the number of standard deviations for the Bollinger Bands.

## Strategy Logic

### Moving Averages

- **200-Period SMA:** Calculated for both the current symbol and the comparative symbol.

### Bollinger Bands Calculation

- **Basis:** 20-period SMA of the closing price.
- **Upper Band:** Calculated as `basis + (mult * standard deviation)`.
- **Lower Band:** Calculated as `basis - (mult * standard deviation)`.

### Long Position

- **Entry Condition:**
  - Enter a long position when the closing price is above the upper Bollinger Band.
  - The comparative symbol's closing price must be above its 200-period SMA.
  - Set the initial trailing stop price below the entry price by the trailing stop percentage.

- **Trailing Stop Update:**
  - Adjust the trailing stop price if the position is profitable and the price moves up.

- **Exit Condition:**
  - Close the long position when the closing price falls below the dynamically calculated trailing stop.
  - OR if the comparative symbol's closing price falls below its 200-period SMA.

## Execution

- **Enter Long:** When the entry conditions are met.
- **Update Stop:** As the price increases, adjust the trailing stop price.
- **Close Long:** When the exit conditions are met.

### Additional Notes
- **Position Size:** Set to 5% of equity to manage risk.
