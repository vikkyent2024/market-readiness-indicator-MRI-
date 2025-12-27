# Technical Design Constraints & Differentiation Guardrails

## Product: Market Readiness Indicator (MRI)
**Platform:** TradingView (Pine Script – Invite-Only / Protected)

---

## 1. Purpose of This Document

This document defines:
- **Hard technical constraints** imposed by TradingView & Pine Script
- **Design guardrails** to prevent over‑engineering
- **Differentiation rules** to ensure we do NOT recreate an existing indicator
- **Explicit DO / DO NOT rules** for AI coding agents (Antigravity, etc.)

This document exists to:
- Prevent building a copy of RSI / MACD / Supertrend / LuxAlgo
- Avoid the “no‑trade / always HOLD” failure mode
- Keep the product novel in **presentation, behavior, and decision framing**

---

## 2. Platform Constraints (Non‑Negotiable)

### 2.1 TradingView / Pine Script Limitations

- No external APIs or data feeds
- No server‑side state beyond bar history
- No database, memory, or user accounts
- No cross‑symbol scanning (Phase 1)
- No true AI / ML models
- Execution is per‑chart, per‑symbol, per‑timeframe

**Design implication:**  
The indicator must derive all insight from **price behavior alone**, using lightweight internal logic.

---

## 3. Intellectual Property Protection Rules

### 3.1 Script Visibility

- Script MUST be **Invite‑Only / Protected**
- Source code must NEVER be shared with users
- No debug plots revealing internal calculations

### 3.2 User‑Facing Transparency

- Users see **outcomes**, not formulas
- Internal logic must be **non‑obvious by visual inspection**

---

## 4. Differentiation Guardrails (CRITICAL SECTION)

This section ensures we **do NOT build something that already exists**.

### 4.1 What Already Exists in the Market (We Must Avoid)

We must NOT recreate or resemble:

- RSI overbought / oversold indicators
- MACD crossover logic
- EMA / SMA cross strategies
- Supertrend flip systems
- Buy / Sell arrow indicators
- ICT / SMC pattern replication
- Volatility bands (BB / Keltner clones)
- “Trend strength” meters tied to a single indicator

If the product can be explained as:
> “It’s basically RSI + X”  

**→ The design has failed.**

---

### 4.2 What Makes This Product DISTINCT

The Market Readiness Indicator is differentiated by:

1. **Decision Framing (NOT Signals)**
   - Outputs *market suitability*, not trade instructions

2. **Behavioral Interpretation**
   - Evaluates interaction of market behaviors, not raw indicator values

3. **Always‑On Context**
   - Never silent
   - Never binary
   - Always informative

4. **Human‑Centric Output**
   - Labels + score, not lines and oscillators

---

## 5. Core Technical Design Rules

### 5.1 Internal Logic Rules

- No hard gating (no IF‑ALL‑TRUE blocks)
- No binary permission logic
- No single indicator dominance
- All internal signals contribute **proportionally**, not absolutely

### 5.2 State Calculation Rules

- States may overlap
- Score must degrade gradually
- Label must be **stickier than score** (hysteresis)

---

## 6. Market Behavior Model (Abstract Only)

⚠️ **These are NOT exposed indicators.**

Internal evaluation MAY reference:
- Price efficiency (movement vs range)
- Volatility regime shifts (expansion vs absorption)
- Momentum decay (participation loss)
- Structural asymmetry (late‑move risk)

But:
- No direct plotting of RSI, MACD, EMA, ATR
- No user‑visible thresholds (e.g. RSI > 70)

---

## 7. Output Constraints (User Experience)

### 7.1 Maximum Complexity Rule

At any moment, the chart may display:
- ONE primary label
- ONE numeric score
- Optional subtle background shading

Anything beyond this is **out of scope**.

---

## 8. Alerting Constraints

- Alerts may trigger on:
  - Label change
  - Score crossing bands

- Alerts must NOT:
  - Say “BUY” or “SELL”
  - Encode strategy logic

---

## 9. Performance & Stability Constraints

- Indicator must run efficiently on:
  - 1m charts
  - Daily charts

- No repainting
- No future data leakage
- No excessive recalculation

---

## 10. Explicit NON‑GOALS (Reconfirmed)

The system must NEVER:

- Claim predictive power
- Optimize for backtests
- Compete with scanners
- Replace trader discretion
- React to news events

---

## 11. AI Coding Agent Instructions (Antigravity‑Safe)

When using this document with AI tools:

- Implement ONLY what is defined
- Do NOT add features “for completeness”
- Do NOT introduce new indicators
- Do NOT expose internal calculations
- Do NOT simplify into known indicator logic

If an instruction violates this doc → **STOP and ask**.

---

## 12. Validation Checklist (Before Release)

Before calling Phase 1 complete:

- Can a trader understand it in <30 seconds?
- Does it provide value even on bad days?
- Does it avoid BUY/SELL language entirely?
- Can it be mistaken for RSI/MACD/Supertrend?  
  - If yes → redesign

---

## 13. Status

**Document Status:** Locked – Phase 1  
**Amendments require deliberate review**

---

*End of Technical Design Constraints & Differentiation Guardrails*

