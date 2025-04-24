# Simple-Trading-Strategy

**Objective:** Demonstrates a basic stock‑trading algorithm to reinforce Python and pandas skills-does not guarantee profits.

**Signals:**

Fast signal (MA10) – 10‑day moving average, sensitive to recent price changes.

Slow signal (MA50) – 50‑day moving average, captures long‑term trends.

**Trading Rule:**

Long 1 share when MA10 > MA50.

Flat (0 shares) otherwise.

**Implementation Steps:**

Generate shares vector via list comprehension: 1 if MA10 > MA50, else 0.

**Compute Profit:**

Calculate Wealth by cumulatively summing daily profits (cumsum).
The “cumulative wealth” series is nothing more than a running total of your strategy’s day-by-day profits. Concretely:

1. **Daily Profit (`Profit`)**  
   - On each trading day *i*, you compute
![image](https://github.com/user-attachments/assets/0890067e-bfab-4d7b-b2d5-1156ab38e671)
   - This gives you one number per day: either the gain (or loss) realized the next day if you held a position, or zero.

2. **Cumulative Wealth (`wealth`)**  
   - You then apply R’s `cumsum()` function to that daily-profit column:  
     ```r
     stk <- stk %>%
       mutate( wealth = cumsum(Profit) )
     ```  
   - Mathematically, at day *t*,
     ![image](https://github.com/user-attachments/assets/699e2e94-b67d-48bb-9bbb-2e8a850d5d5f)
   - In other words, you’re incrementally adding each day’s net gain/loss to the previous total, so that `wealth_t` represents the total P&L the strategy would have realized up to date *t*.

3. **Interpretation Over Time**  
   - Plotting `wealth` vs. `Date` gives you the equity-curve of the strategy—showing how your pocket (or account) would have grown (or shrunk) over the backtest window.  
   - The final value (`last(stk$wealth)`) is simply the total money “won” (net of losses) by the end of your dataset.

![image](https://github.com/user-attachments/assets/f07d54da-efea-4120-ab2a-8afcc08a2561)
