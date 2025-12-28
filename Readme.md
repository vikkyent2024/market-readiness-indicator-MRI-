# Market Readiness Indicator (MRI) — v1.0

**Status:** Locked / Stable Release
**Purpose:** Educational market-timing indicator (NOT a buy/sell system)

---

## 1. What MRI Is (and Is Not)

**MRI IS:**

* A market *health* and *timing* indicator
* Designed to answer **WHEN** conditions are favorable
* Retail-safe and non-directive

**MRI IS NOT:**

* An entry/exit system
* A signal generator
* A replacement for strategy rules

---

## 2. Core Concept

MRI separates decision-making into two independent dimensions:

* **WHEN** → Market Readiness (trend + volatility health)
* **WHERE** → Price Location (Support / Resistance)

A trade is valid **only when BOTH align**.

---

## 3. Pullback Score (pb_score: 0–100)

The Pullback Score measures whether the market is behaving in a *tradable* manner.

### Components (Internal Logic — Fixed)

1. **Pullback Depth vs EMA50** (ATR-normalized)
2. **Volatility Stability** (current ATR vs average ATR)
3. **Trend Efficiency** (Kaufman Efficiency Ratio)

### Interpretation

* **pb_score ≥ 60** → Market Conditions Favorable
* **pb_score < 60** → Market Conditions Unstable

> This score evaluates *market behavior*, not price location.

---

## 4. MRI State Labels

### Primary Status Label

* **WAIT – Market Conditions Favorable**
* **WAIT – Market Conditions Unstable**

### Subtext Guidance

* Explains *why* conditions are favorable or unstable
* Explicitly states that **entry depends on Support / Resistance**

This prevents accidental “buy now” interpretation.

---

## 5. Institutional Support & Resistance System

### Purpose

Provides **spatial context** only — answers **WHERE price is**.

### Methodology

* Fractal-based swing detection
* Clustered into zones using ATR-based proximity
* Zones persist until invalidated by price

### Zone Types

* **Institutional Demand (Support)**
* **Institutional Supply (Resistance)**

---

## 6. Support & Resistance Labels

Each zone label displays:

* Zone type (Support / Resistance)
* Exact price level
* % distance from current price
* Directional context (Above / Below)
* Market context text

### Example

* "1.8% Above Current Price – Active Overhead Supply"
* "0.1% Below Current Price – Support Under Test"

---

## 7. Broken Support / Resistance Logic

MRI does **not** assume a level is valid forever.

### When Support Is Broken

* Label updates to reflect failure
* Messaging changes to:

  * "Support Broken"
  * "Reclaim Required"
* MRI **does NOT** override this with bullish messaging

This prevents false confidence during breakdowns.

---

## 8. Timeframe Behavior (Important)

MRI recalculates **independently per timeframe**.

* **Lower TF (e.g., 1H):** Tactical tradability
* **Higher TF (e.g., Daily/Weekly):** Structural health

### Result

It is normal for:

* Lower TF = Favorable
* Higher TF = Unfavorable

This is **expected behavior**, not a bug.

---

## 9. How to Use MRI Correctly

### Valid Trade Checklist

1. MRI = Market Conditions Favorable
2. Price location =

   * At support (with confirmation), OR
   * Above reclaimed resistance
3. Higher timeframe not in conflict

If ANY item fails → **WAIT**

---

## 10. What MRI Protects You From

* Chasing extended price
* Buying into resistance
* Trading during unstable volatility
* Confusing momentum with opportunity

---

## 11. Versioning

* **v1.0** — Locked baseline release
* Future updates must be **additive only**
* No retroactive logic changes

---

## 12. Final Philosophy

> MRI does not tell you *what* to trade.
> MRI tells you *when trading is allowed*.
> Location decides *whether you act*.

This design is intentional, professional, and retail-safe.
