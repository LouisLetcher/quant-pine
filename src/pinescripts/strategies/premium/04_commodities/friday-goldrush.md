# Friday Gold Rush (FGR) Strategy

The **Friday Gold Rush (FGR) Strategy** is designed to capitalize on short-term momentum in the gold market by entering trades on Thursdays or Fridays when the gold price rises significantly. This strategy employs leverage, trailing stops, and specific exit logic to maximize potential gains while managing risks effectively.

---

## Inputs

- **Leverage:** The degree of leverage applied to trades, adjustable from 1 to 100 (default: 75).
- **Trailing Stop Distance:** The distance, in points, for the trailing stop to lock in profits as the price moves (default: 5 points).
- **Gold Rise Threshold:** The minimum percentage increase in gold price required for a trade entry (default: 0.5%).
- **Gold Symbol:** The asset symbol representing gold (e.g., XAUUSD), user-defined for flexibility (default: "XAUUSD").
- **Entry Day of Week:** The specific day of the week for trade entry, typically Thursday (5) or Friday (6).

---

## Strategy Logic

### Core Logic
- **Gold Price Movement:** Tracks the percentage change in the gold price on a daily basis.
- **Entry Conditions:**
  - **Thursday Entry:** If the gold price rises by more than the specified threshold on Thursday.
  - **Friday Entry:** If the gold price rises by more than the specified threshold on Friday.
- **Exit Conditions:**
  - Trailing stop triggered by adverse price movements.
  - Automatic exit on Monday, unless a strong trend continues.

---

## Execution

### Trade Entry
- **Long Entry:** Triggered when the price rise exceeds the threshold on Thursday or Friday.
- **Entry Signal Visualization:** Marked on the chart with upward-facing green arrows for clarity.

### Trade Management
- **Trailing Stop:** Automatically adjusts as the price moves favorably, ensuring profits are locked in while allowing for further gains.
- **Monday Exit:** Any open positions are closed early on Monday to mitigate risks associated with holding over the weekend.

### Trade Exit
- **Trailing Stop Triggered:** Exit occurs when the price falls below the trailing stop level.
- **Manual Exit Logic:** Positions are also closed manually if specific conditions, such as exceeding the trailing stop distance, are met.

---

## Visual Representation
- **Gold Price Plot:** Displays the gold price as a yellow line for reference.
- **Trailing Stop Level:** Represented by a red line, dynamically adjusted based on price movement.
- **Entry Signals:** Green arrows indicate points where long positions are initiated.

---

## Additional Notes
- **High Leverage:** Designed for use with high leverage, emphasizing short-term trades.
- **Customizable Inputs:** Allows flexibility in adapting the strategy to different market conditions or trading preferences.
- **Risk Management:** Employs robust trailing stop mechanisms to manage risk effectively.

The **Friday Gold Rush Strategy** is ideal for traders seeking to exploit gold market momentum during specific days of the week, with a focus on disciplined exits and profit protection.
