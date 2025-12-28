# Market Readiness Indicator (MRI) - V1 Features Guide (Frozen)

## 🚀 Core Philosophy

The **Market Readiness Indicator (MRI)** is an institutional-grade **Trading Permission Engine**.
It answers exactly one question: **"What type of trading is allowed in the current market state?"**

It is designed to be **Opportunity-Preserving**, not restrictive. It acts as a "Mode Selector" for your strategy.

---

## 🚦 The 5 Market States (V1 Semantics)

The MRI classifies the market into 5 distinct permission states.

| State | Color | Definition | Allowed Trading Behavior |
| :--- | :--- | :--- | :--- |
| **LONG – Trend Active** | 🟢 **Green** | **Trend + Momentum Aligned.** Market is structurally bullish and high-quality. | **Aggressive Longs Allowed.** Hold winners, buy breakouts, add to positions. |
| **SHORT – Trend Active** | 🔴 **Red** | **Trend + Momentum Aligned.** Market is structurally bearish and high-quality. | **Aggressive Shorts Allowed.** Hold winners, sell breakdowns, add to positions. |
| **WAIT – Pullback / Reset** | 🟠 **Orange** | **Trend Intact, Momentum Paused.** Price is extended or consolidating, but the trend is NOT broken. | **Mean Reversion / Pullback Buys ONLY.** Do not chase breakouts. Look for dips to value. |
| **NO EDGE – Chop** | ⚪ **Grey** | **Structure Degrading.** No clear directional bias or low efficiency. | **Diffensive / Reduced Size.** Avoid new entries. Tighten stops. |
| **AVOID – High Risk** | 🟣 **Purple**| **Structural Break / Extreme Risk.** Flash crash or volatility shock. | **Cash / Hedge.** No directional trades. |

---

## 🛡️ Algo & Strategy Integration rules

If using the MRI in an automated or discretionary system, follow these integration rules:

### 1. The "WAIT" Rule (Critical)

* **Old Retail Thinking**: "Wait means stop."
* **Institutional MRI Logic**: "Wait means **Trend Continuation Zone**."
* **Action**: If you see `WAIT` in a Bull Trend, you are **allowed** to buy support/dips. You are **blocked** from buying high breakouts.

### 2. State Logic

* **LONG** = Permission for **Momentum** Strategies.
* **WAIT** = Permission for **Mean Reversion** Strategies.
* **NO EDGE** = Permission for **Range** Strategies (if advanced) or Cash.

### 3. Stability Guardrails

* **No Flipping**: MRI will never flip Green → Red directly. It respects market inertia.
* **Graceful Degradation**: Trends fade to WAIT before failing to NO EDGE.

---

## 📋 Technical Specs (V1)

* **Platform**: TradingView (Pine Script v5)
* **Logic**: 5-State Semantic Model (Bias + Quality + Extension)
* **Version**: V1 (Frozen)

> *"This indicator defines trade mode, not trade entry."*
