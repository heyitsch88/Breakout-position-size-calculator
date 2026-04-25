# Breakout Prop Position Size & Fee Calculator

An advanced, fee-adjusted position size calculator built specifically for the strict equity limits and leverage caps of [Breakout Prop](https://www.breakoutprop.com/) evaluations.

Unlike standard position size calculators that strictly use entry and stop-loss distance, this tool **reverse-engineers exchange fees** to ensure your total loss never exceeds your strict drawdown limits.

## 🚀 Features

* **Fee-Adjusted Position Sizing:** Automatically calculates sizing so that your pure price loss + entry fee + stop-loss fee perfectly equals your exact risk budget.

* **Strict Drawdown Guardrails:** Calculates both your Daily Loss Limit (based on 00:30 UTC balance) and Static Max Drawdown to highlight your Active Breach Level.

* **Leverage & Margin Safety Checks:** Built-in checks for Breakout's specific leverage caps (5x for BTC/ETH, 2x for Altcoins) to prevent margin rejection errors.

* **Terminal-Accurate Lot Flooring:** Floors position sizes to `0.001` lots to perfectly match real-world broker execution conditions.

* **Dark / Light Mode:** Fully responsive UI with a seamless theme toggle that saves your preference.

## 🛠️ Usage

This application is built as a single, fully standalone `index.html` file with zero dependencies (styling via CDN Tailwind CSS).

**To run locally:**

1. Clone this repository or download the `index.html` file.

2. Double-click `index.html` to open it in any modern web browser.

## 🧮 How the Math Works

Standard calculators tell you how many units to buy based strictly on the distance between your entry and stop. However, when the stop is hit, you pay an entry fee *and* an exit fee. In a prop trading environment, this hidden fee can cause your actual loss to exceed your risk budget, potentially breaching your account.

This calculator uses the following reverse-engineered logic:
`Size = Target Risk / (SL Distance + (Entry Price * Fee Rate) + (Stop Price * Fee Rate))`

It then floors the result to `0.001` lots to ensure your total verified loss will slightly under-risk your target, keeping your account safe.

## ⚠️ Disclaimer

Built by [heyitsch](https://x.com/heyitsCH).

**Not financial advice.** This tool provides a mathematical position size estimate. Sizing assumes no slippage or spread change. In live market conditions, negative slippage, exchange fees, swap fees, and gap-downs can cause your actual loss to exceed your estimated risk. Always use this in conjunction with your live Breakout Dashboard equity tracking. Breakout is not responsible if slippage occurs and/or losses exceed the numbers outlined in the calculator.
