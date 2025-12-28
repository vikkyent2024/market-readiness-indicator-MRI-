# Market Readiness Indicator (MRI) - Features Guide

## 🚀 Core Philosophy

The **Market Readiness Indicator (MRI)** is a professional **Trading Permission Engine**. Unlike standard indicators that spam "Buy/Sell" signals, the MRI answers the most important question in trading:

> **"Is the market environment safe to trade right now, and in which direction?"**

It prevents overtrading by strictly defining when you have **Edge** and when you should **Sit Out**.

---

## 🚦 The 5 Market States

The MRI classifies every candle into one of 5 clear semantic states.

| State | Color | Definition | Action Rule |
| :--- | :--- | :--- | :--- |
| **LONG – Trend Active** | 🟢 **Green** | **Bullish Trend + High Quality.** The market is moving up efficiently and is not properly exhausted. | **Look for BUYS.** Ignore sell signals. |
| **SHORT – Trend Active** | 🔴 **Red** | **Bearish Trend + High Quality.** The market is moving down efficiently and is not properly exhausted. | **Look for SELLS.** Ignore buy signals. |
| **WAIT – Pullback / Reset** | 🟠 **Orange** | **Trend Paused.** The market has directional bias but is either over-extended or temporarily consolidating. | **HOLD / MANAGE.** Do not enter new positions. Wait for Green/Red or Gray. |
| **NO EDGE – Chop** | ⚪ **Grey** | **No Direction.** The market is chopping sideways with low efficiency and unclear bias. | **DO NOT TRADE.** Protect capital. |
| **AVOID – High Risk** | 🟣 **Purple**| **Extreme Volatility.** Flash crash, news spike, or pump/dump action detected. | **STAY OUT.** High risk of slippage and whipsaw. |

---

## 🛡️ Smart Logic & Safety Guardrails

### 1. No "Signal Flipping"

The MRI will **never** flip directly from **LONG** to **SHORT** (or vice versa).

* It enforces a logical market cycle: `Trend -> Wait -> Chop -> New Trend`.
* This prevents you from getting caught in "whipsaws" at the top or bottom of moves.

### 2. Graceful Degradation

Trends don't just disappear instantly.

* If a strong trend weakens, the MRI downgrades it to **WAIT** first, giving you time to manage stops or take profit.
* It will only go to **NO EDGE** if the market actively loses its directional structure.

### 3. "Stickiness" & Stability

* **2-Bar Confirmation**: A new state must persist for 2 consecutive bars before the signal changes. This eliminates flickering on live candles.
* **No Repainting**: Once a bar closes, the state is locked. It will never change retroactively.

### 4. Volatility Protection

* The indicator automatically detects "Exhaustion" (when price moves too far from the average) and switches to **WAIT**, preventing you from buying the absolute top or selling the absolute bottom.

---

## 📉 How to Use in Your Strategy

The MRI is **not** a strategy itself; it is a filter for *your* strategy.

1. **If MRI is GREEN**: You have permission to trade your Bullish Setup (e.g., Bull Flag, Breakout, Support Bounce).
2. **If MRI is RED**: You have permission to trade your Bearish Setup (e.g., Bear Flag, Breakdown, Resistance Reject).
3. **If MRI is GREY/ORANGE**: You sit on your hands. **Preserving capital is a trading position.**

---

## 📋 Technical Specs

* **Platform**: TradingView (Pine Script v5)
* **Overlay**: Yes (Background Tint + dashboard)
* **Timeframes**: Works on all timeframes (best on 5m, 15m, 1H, 4H).
* **Asset Class**: Stocks, Crypto, Forex, Futures.

---

> *"This indicator defines when to trade, not how to enter."*
