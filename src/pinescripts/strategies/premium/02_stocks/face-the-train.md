# Face the Train Strategy

The **Face the Train Strategy** is designed to identify and capitalize on market trends based on consecutive bullish or bearish price movements. This strategy uses simple moving averages (SMA) and a sequence counter to confirm the strength of trends before entering long or short positions.

---

## Inputs

- **Short-term SMA Period:** Defines the period for calculating the short-term SMA to guide trade exits (default: 9).
- **Consecutive Bullish Days Threshold:** The required number of consecutive bullish days to trigger a long entry (default: 1).
- **Consecutive Bearish Days Threshold:** The required number of consecutive bearish days to trigger a short entry (default: 1).
- **Initial kb Value:** Initial value for the bullish sequence counter (default: 0).
- **Initial mb Value:** Initial cumulative count for bullish sequences (default: 0).
- **Initial kbs Value:** Initial value for the bearish sequence counter (default: 0).
- **Initial mbs Value:** Initial cumulative count for bearish sequences (default: 0).

---

## Strategy Logic

### Long Position
- **Entry Condition:**
  - The closing price must be higher than the previous day for a specified number of consecutive days.
  - The cumulative bullish sequence counter (`mb`) reaches the threshold (`numb + 1`).
  - The closing price is above the 200-period SMA, indicating a long-term uptrend.
- **Exit Condition:**
  - The closing price rises above the short-term SMA, signaling the end of the trend or an overbought condition.

### Short Position
- **Entry Condition:**
  - The closing price must be lower than the previous day for a specified number of consecutive days.
  - The cumulative bearish sequence counter (`mbs`) reaches the threshold (`numbs + 1`).
  - The closing price is below the 200-period SMA, indicating a long-term downtrend.
- **Exit Condition:**
  - The closing price falls below the short-term SMA, signaling the end of the trend or an oversold condition.

---

## Execution

### Trade Entry
- **Long Entry:** Triggered when the bullish sequence threshold is met, and the price is above the 200-period SMA.
- **Short Entry:** Triggered when the bearish sequence threshold is met, and the price is below the 200-period SMA.

### Trade Exit
- Long positions are closed when the closing price is above the short-term SMA.
- Short positions are closed when the closing price is below the short-term SMA.

---

## Visual Representation
- **Bullish and Bearish Counters:** Internal logic tracks consecutive bullish and bearish days to determine trend strength.
- **Short-term SMA Plot:** Acts as a dynamic guide for exiting trades.
- **Entry and Exit Signals:**
  - **Green "BUY" Labels:** Indicate long position entries.
  - **Red "SELL" Labels:** Indicate position exits.

---

## Additional Notes

- **Trend Following:** This strategy is well-suited for trend-following traders who aim to ride strong trends in either direction.
- **Customizable Parameters:** Input parameters allow for flexibility in defining trend thresholds and SMA periods to suit different market conditions.
- **Risk Management:** Ensures positions are aligned with prevailing trends, reducing the likelihood of premature entries or exits.

The **Face the Train Strategy** is an effective tool for identifying strong directional moves and managing trades with a disciplined, trend-based approach.
