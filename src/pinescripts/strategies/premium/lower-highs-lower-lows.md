# Lower Highs & Lower Lows Strategy

This strategy aims to identify potential short-term trading opportunities by detecting a simple price pattern: consecutive bars where both the highs and lows are lower than those of the previous bar. When such a pattern occurs, the strategy enters a long position and holds it for a predefined number of days before automatically closing it.

## Inputs

- **Exit After N Days (`holdingDays`):**
  Defines how long the strategy will hold a position before it automatically exits. The default value is 1 day, but it can be adjusted depending on the trader’s time horizon.

## Strategy Logic

### Condition: Lower High & Lower Low

- **Lower High & Lower Low Pattern:**
  The strategy checks if today’s high is lower than yesterday’s high, and today’s low is lower than yesterday’s low. This suggests a short-term trend where the market is continuously moving lower on both ends of the daily range.

### Long Position Entry

- **Entry Condition:**
  If the identified pattern (lowerHighLow) occurs and the strategy is not currently in a position, the strategy initiates a long position. The logic here is contrarian: after a consecutive lower-high-lower-low pattern, the strategy expects a short-term rebound.

### Position Exit

- **Timed Exit:**
  The strategy does not rely on price-based stops or targets. Instead, it uses a time-based exit. After holding the position for `holdingDays` bars, the position is closed automatically. This ensures that the strategy remains in the trade only for a short, predefined duration, regardless of price action.

## Execution Flow

1. **Check Condition:** For each new bar, determine if the high and low are both lower than the previous bar’s highs and lows.
2. **Enter Long:** If this condition is true and no position is currently held, enter a long position.
3. **Track Time in Trade:** Once in a trade, count how many bars have passed.
4. **Exit After N Days:** Close the position automatically once the specified `holdingDays` threshold is reached.

## Additional Notes

- **Position Sizing:** The strategy is set to use 100% of equity for each trade, which can be aggressive. Adjust this setting as needed to fit your risk management parameters.
- **Customization:** The `holdingDays` input can be fine-tuned. Shorter holding periods may suit more volatile markets, while longer periods may be useful for less volatile conditions.
