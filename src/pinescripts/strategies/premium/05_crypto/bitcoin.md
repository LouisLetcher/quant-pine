# Bitcoin Strategy

This Pine Script strategy is designed for trading Bitcoin by entering and exiting long positions based on specific conditions related to price movement and a simple moving average (SMA).

## Inputs

- **Lookback Period:** Defines the period over which the current close price is compared to the historical close price.
- **Moving Average Period:** Defines the period used to calculate the Simple Moving Average (SMA).

## Strategy Logic

### Entry Condition

- **Enter Long Position:**
  - The current close price must be higher than the close price `Lookback Period` days ago.
  - The current close price must also be higher than the SMA calculated over the `Moving Average Period`.

### Exit Condition

- **Close Long Position:**
  - The current close price falls below the close price `Lookback Period` days ago.
  - OR the current close price falls below the SMA calculated over the `Moving Average Period`.

## Execution

- **Enter Long:** When the entry condition is met.
- **Exit Long:** When the exit condition is met.
