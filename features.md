# Market Readiness Indicator (MRI) - V1 Technical Documentation

## 🚀 Core Philosophy

The **Market Readiness Indicator (MRI)** is an institutional-grade **Trading Permission Engine**.
It answers exactly one question: **"What type of trading is allowed in the current market state?"**

It is designed to be **Opportunity-Preserving**, not restrictive. It acts as a "Mode Selector" for your strategy.

---

## 🚦 Visual Control Center & Permissions

The MRI uses a simple Traffic Light system to communicate permissions instantaneously.

| State | Background Color | Label Text | Allowed Trading Mode |
| :--- | :--- | :--- | :--- |
| **LONG** | 🟢 **Dark Green** | `LONG - Trend Active` | **Momentum / Continuation.**<br>• Buy Breakouts<br>• Buy Strength<br>• Add to Winners |
| **SHORT** | 🔴 **Dark Red** | `SHORT - Trend Active` | **Momentum / Continuation.**<br>• Sell Breakdowns<br>• Sell Weakness<br>• Add to Winners |
| **WAIT (GOOD)** | 🟢 **Light Green** | `WAIT - Pullback (GOOD)` | **Mean Reversion / Dips.**<br>• Buy Support / Pullbacks.<br>• Trend is valid, price is discounted.<br>• **Best Entry Time.** |
| **WAIT (BAD)** | 🟠 **Orange** | `WAIT - Pullback (BAD)` | **Caution.**<br>• Pullback is too deep or volatile.<br>• Wait for stability or price to reclaim structure. |
| **NO EDGE** | ⚪ **Grey** | `NO EDGE` | **Defensive.**<br>• Reduce Size.<br>• Tighten Stops.<br>• No new directional bets. |
| **AVOID** | 🟣 **Purple** | `AVOID` | **Cash / Hedge.**<br>• Extreme volatility event.<br>• Stay out. |

---

## ⚙️ Technical Architecture (Internal Logic)

The MRI derives these states from 4 non-correlated market dimensions.

### 1. Directional Bias layer

* **Indicator Used:** `EMA (50 Period)` + Slope Logic.
* **Logic:**
  * **Bullish:** Price > EMA 50 AND EMA 50 Slope > 0.
  * **Bearish:** Price < EMA 50 AND EMA 50 Slope < 0.

### 2. Market Quality Layer

* **Indicator Used:** `Kaufman Efficiency Ratio (ER)` (14 Period).
* **Why:** Removes "Noise". It distinguishes between a "clean trend" and "choppy drift".
* **Threshold:** `ER > 0.30` is required for `LONG`/`SHORT` states. Lower values force the system into `WAIT` or `NO EDGE`.

### 3. Volatility & Risk Layer

* **Indicator Used:** `ATR (Average True Range)` (14 Period).
* **Logic:**
  * **Vol Spike:** If current ATR > 2.5x the 50-bar Average ATR, the system triggers `AVOID` (Purple). This detects flash crashes or news shocks.
  * **Pullback Scoring:** Uses ATR to determine if a pullback is "shallow" (safe) or "deep" (risky).

### 4. Extension Layer

* **Indicator Used:** `Bollinger Bands` (50 Period, 2.2 SD).
* **Logic:** If price exceeds the 2.2 Standard Deviation bands, the market is "Overextended". The system forces a `WAIT` state to prevent buying the exact top or selling the exact bottom.

---

## 🛡️ Algo & Strategy Integration rules

### The "WAIT" State (Critical Concept)

* **Old Retail Thinking**: "Wait means stop."
* **Institutional MRI Logic**: "Wait means **Trend Continuation Zone**."
* **Action**: If you see `WAIT` in a Bull Trend, you are **allowed** to buy support/dips. You are **blocked** from buying high breakouts.

### Stability Guardrails

* **No Flipping**: MRI will never flip Green → Red directly. It respects market inertia.
* **Graceful Degradation**: Trends fade to WAIT before failing to NO EDGE.

---

## 🆕 Advanced Features (Optional Modules)

### 1. Wait Quality Scoring (Pullback Score)

A 0-100 Score displayed in the table subtitle.

* **Score > 60**: `WAIT (GOOD)` (Light Green). Safe to enter.
* **Score < 60**: `WAIT (BAD)` (Orange). Risky.

### 2. Pullback Opportunity Gating (Strict Mode)

*(Input: `Enable Strict Pullback Gating`)*

Prevents overtrading in long trends.

* **Actionable**: The *first* qualified pullback in a leg is marked `(ACTIONABLE)`.
* **Cooldown**: Subsequent signals are marked `(COOLDOWN)` until the trend makes a new high/low.

### 3. Institutional Liquidity Zones (Auto-S/R)

Professional support/resistance boxes.

* **Logic**: Uses **Fractals** to find pivots and **Clusters** them (within 0.75 ATR).
* **Validation**: A zone must have **3+ price reactions** to appear.
* **Visibility**: Only visible when trading is allowed (`LONG` or `WAIT-GOOD`).

### 4. Entry Triggers (Optional)

*(Inputs: `Enable Pullback Triggers`, `Trigger: EMA Reclaim`, `Trigger: Structure Break`)*

If enabled, text notifications appear in the table when:

* **EMA Reclaim**: Price crosses back over EMA 21.
* **Structure Break**: Price breaks the 5-bar structure high/low.

---

## 📋 Technical Specs

* **Platform**: TradingView (Pine Script v5)
* **Logic**: 5-State Semantic Model (Bias + Quality + Extension)
* **Repainting**: **NONE**. All logic confirms on bar close.
