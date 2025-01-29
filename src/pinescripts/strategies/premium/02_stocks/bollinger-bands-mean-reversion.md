# Bollinger Bands Mean Reversion Strategy

The **Bollinger Bands Mean Reversion Strategy** is designed to identify potential market reversals and capitalize on price movements that deviate significantly from their average value, as indicated by Bollinger Bands. This strategy combines technical indicators with predefined risk management parameters to execute trades effectively.

---

## Inputs

- **Bollinger Bands Length:** The number of periods used to calculate the moving average (default: 20).
- **Bollinger Bands StdDev:** The number of standard deviations used to calculate the upper and lower bands (default: 2.0).
- **Take Profit (pips):** The desired profit level for each trade, expressed in pips (default: 50).
- **Stop Loss (pips):** The maximum allowable loss for each trade, expressed in pips (default: 20).
- **Pip Value:** The value of one pip in price terms (default: 0.0001).

---

## Strategy Logic

### Core Indicators
- **Bollinger Bands:**
  - **Middle Band:** A simple moving average (SMA) calculated over the specified length.
  - **Upper Band:** The middle band plus a multiple of standard deviation (StdDev).
  - **Lower Band:** The middle band minus a multiple of standard deviation (StdDev).

### Long Position
- **Entry Condition:**
  - The closing price crosses below the lower Bollinger Band, signaling a potential mean reversion opportunity.
- **Exit Condition:**
  - A take profit or stop loss level is reached.

### Short Position
- **Entry Condition:**
  - The closing price crosses above the upper Bollinger Band, signaling a potential mean reversion opportunity.
- **Exit Condition:**
  - A take profit or stop loss level is reached.

---

## Execution

### Trade Entry
- **Long Entry:** Triggered when the price crosses under the lower Bollinger Band.
- **Short Entry:** Triggered when the price crosses over the upper Bollinger Band.

### Risk Management
- **Take Profit (TP):** Calculated based on the specified number of pips above the entry price for long positions or below the entry price for short positions.
- **Stop Loss (SL):** Calculated based on the specified number of pips below the entry price for long positions or above the entry price for short positions.

### Trade Exit
- When a take profit or stop loss condition is met, the trade is automatically exited.

---

## Visual Representation
- The strategy plots the Bollinger Bands (upper, middle, and lower) on the price chart for clarity
