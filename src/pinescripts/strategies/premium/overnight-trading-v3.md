# Overnight Trading Strategy - Variant 3

The **Overnight Trading Strategy - Variant 3 (OTS V3)** is designed to capture short-term gains by entering a long position when the Relative Strength Index (RSI) indicates oversold conditions. Trades are automatically exited at the next day's open, ensuring minimal exposure and consistent overnight trading.

---

## Inputs

- **RSI Length:** The number of periods used for RSI calculation (default: 2).
- **RSI Threshold:** The RSI value below which a long position is initiated, signaling oversold conditions (default: 10).

---

## Strategy Logic

### Core Indicators
- **Relative Strength Index (RSI):**
  - Calculated using the specified RSI length.
  - A value below the threshold indicates a potential buying opportunity.

### Long Position
- **Entry Condition:**
  - The RSI value falls below the defined threshold, indicating oversold conditions and a possible price rebound.
- **Exit Condition:**
  - The position is closed at the next day's open, regardless of price movement.

---

## Execution

### Trade Entry
- **Long Entry Trigger:** A long position is opened when the RSI value is below the specified threshold.
- **Signal Visualization:**
  - A **green label** ("BUY") is displayed below the bar where the long position is initiated.

### Trade Exit
- **Exit Trigger:** The position is automatically closed at the next day's open.
- **Signal Visualization:**
  - A **red label** ("SELL") is displayed above the bar where the position is exited.

---

## Visual Representation

- **RSI Plot:** Displays the RSI value as an orange line for real-time monitoring.
- **RSI Threshold:** A horizontal red dotted line marks the oversold threshold.
- **Entry Signals:** Green "BUY" labels below bars indicate where long positions are entered.
- **Exit Signals:** Red "SELL" labels above bars indicate where positions are exited.

---

## Additional Notes

- **Position Size:** The strategy allocates 100% of account equity for each trade, making full use of available capital.
- **Risk Management:** By exiting trades at the next day's open, the strategy minimizes overnight holding risks.
- **Overlay:** The strategy is displayed directly on the price chart for intuitive visualization.

The **Overnight Trading Strategy - Variant 3** is ideal for traders seeking to exploit short-term price recoveries in oversold conditions while maintaining disciplined trade exits.
