# Simple-Trading-Strategy

**Objective:** Demonstrates a basic stock‑trading algorithm to reinforce Python and pandas skills-does not guarantee profits.

**Signals:**

Fast signal (MA10) – 10‑day moving average, sensitive to recent price changes.

Slow signal (MA50) – 50‑day moving average, captures long‑term trends.

**Trading Rule:**

Long 1 share when MA10 > MA50.

Flat (0 shares) otherwise.

Visualized as a highlighted “buy‑and‑hold” region on the price chart.

**Implementation Steps:**

Generate shares vector via list comprehension: 1 if MA10 > MA50, else 0.

**Compute Profit:**

If holding (shares = 1), tomorrow’s close minus today’s close.

If flat, zero.

Calculate Wealth by cumulatively summing daily profits (cumsum).

![image](https://github.com/user-attachments/assets/f07d54da-efea-4120-ab2a-8afcc08a2561)
