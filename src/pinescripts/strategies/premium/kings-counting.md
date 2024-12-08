# King's Counting Strategy

The **King's Counting Strategy** is a momentum and trend-based trading strategy that leverages the DeMark 9-13 sequence to identify phases in market movements. The strategy generates long and short signals based on specific entry criteria, complemented by stop loss and take profit mechanisms to manage risk and secure profits. It operates on a daily timeframe and allocates 100% of equity for each trade.

---

## Inputs

- **Momentum Phase Length:** Defines the number of bars used to calculate the momentum phase (default: 9).
- **Trend Phase Length:** Defines the number of bars used to calculate the trend phase (default: 13).
- **Stop Loss (points):** The distance, in points, for setting the stop loss level (default: 20).
- **Take Profit (points):** The distance, in points, for setting the take profit level (default: 30).

---

## Strategy Logic

### Momentum Phase
- **Momentum Up:** Triggered when the closing price exceeds the highest close in the last 9 bars (momentum length).
- **Momentum Down:** Triggered when the closing price is below the lowest close in the last 9 bars.

### Trend Phase
- **Trend Up:** Confirmed when the close exceeds the highest close of the last 13 bars (trend length).
- **Trend Down:** Confirmed when the close is below the lowest close of the last 13 bars.

### Combined Phases
- **Long Signal:**
  - Momentum is transitioning from down to up.
  - Price is above the trend phase (trend up).
- **Short Signal:**
  - Momentum is transitioning from up to down.
  - Price is below the trend phase (trend down).

---

## Execution

### Trade Entry
- **Long Entry:**
  - Triggered when the combined momentum and trend conditions for an upward movement are met.
- **Short Entry:**
  - Triggered when the combined momentum and trend conditions for a downward movement are met.

### Stop Loss and Take Profit
- **Long Position:**
  - Stop Loss: Set below the entry price by the specified stop loss value.
  - Take Profit: Set above the entry price by the specified take profit value.
- **Short Position:**
  - Stop Loss: Set above the entry price by the specified stop loss value.
  - Take Profit: Set below the entry price by the specified take profit value.

### Trade Exit
- Positions are exited when:
  - **Long Positions:** Price falls below the stop loss or rises above the take profit level.
  - **Short Positions:** Price rises above the stop loss or falls below the take profit level.

---

## Visual Representation

- **Entry Signals:**
  - **Green "BUY" Labels:** Indicate long position entries.
  - **Red "SELL" Labels:** Indicate short position entries.
- **Stop Loss and Take Profit Levels:** Plotted on the chart for both long and short positions.
- **Momentum and Trend Phases:** Visualized to help confirm trading signals.

---

## Additional Notes

- **Risk Management:** The strategy ensures that each trade is equipped with stop loss and take profit mechanisms to minimize risk.
- **Customizability:** Input parameters for momentum and trend phases allow users to adapt the strategy to different market conditions.
- **Daily Timeframe:** Suitable for traders looking for end-of-day trading opportunities.

The **King's Counting Strategy** is a robust tool for traders aiming to exploit momentum shifts and sustained trends in the market, ensuring disciplined entries and exits for optimal risk-reward management.
