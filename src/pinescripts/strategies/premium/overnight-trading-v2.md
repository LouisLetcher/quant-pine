# Overnight Trading Strategy - Variant 2

The **Overnight Trading Strategy - Variant 2 (OTS V2)** is designed to take advantage of overnight market movements by entering trades at the close of the current bar and exiting at the close of the following day. This strategy is straightforward, focusing on capturing potential overnight gains with minimal complexity.

---

## Strategy Logic

### Long Position
- **Entry Condition:**
  - A long position is initiated at the current bar's close when the bar is confirmed.
- **Exit Condition:**
  - The position is closed at the next day's close.

### Trade Flow
1. **Entry:** A long position is opened at the current bar's close.
2. **Exit:** The position is automatically closed at the next day's close to lock in overnight gains or mitigate potential risks.

---

## Execution

### Trade Entry
- **Entry Trigger:** Trades are triggered when the bar is confirmed, indicating the close of the trading session.
- **Signal Visualization:**
  - A **green label** ("BUY") appears below the price bar where the trade is entered.

### Trade Exit
- **Exit Trigger:** The position is closed automatically at the next day's close.
- **Signal Visualization:**
  - A **red label** ("SELL") appears above the price bar where the trade is exited.

---

## Visual Representation
- **Entry Signals:** Green "BUY" labels below the bars indicate where long positions are entered.
- **Exit Signals:** Red "SELL" labels above the bars indicate where positions are exited.

---

## Additional Notes
- **Position Size:** The strategy allocates 100% of the account equity for each trade by default, ensuring full utilization of available capital.
- **Risk Management:** While the strategy does not include stop-loss or take-profit mechanisms, trades are exited within one trading day to limit exposure.
- **Overlay:** The strategy operates directly on the price chart, making it easy to visualize trade activity.

The **Overnight Trading Strategy - Variant 2** is ideal for traders seeking to capitalize on short-term overnight price movements while maintaining a disciplined exit at the next day's close.
