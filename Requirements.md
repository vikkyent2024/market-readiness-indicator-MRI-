Product Requirements Document (PRD)
Product Name: Market Readiness Indicator (MRI)

A Market Readiness & Trade Permission Indicator for discretionary traders (stocks, crypto, options) that avoids chop, highlights opportunity windows,
and warns when risk is increasing — without giving entries.

1. Purpose of This Document
This document serves as the single source of truth for the design, scope, and intent of the Market Readiness Indicator.
It is intended to: - Preserve product context across chats, tools, and future iterations - Be reusable in Antigravity / IDEs / AI coding agents - Prevent scope creep and over‑engineering - Ensure the product does not repeat past failures (over‑filtering, no‑trade behavior)
This document is written from the combined perspective of: - Senior Trader (20+ years discretionary trading) - Senior Software Engineer - Senior Product Manager / Business Analyst

2. Product Vision
One‑sentence vision:

> Provide traders with a clear, confidence‑building assessment of whether current market conditions are worth trading — without giving buy/sell signals.
The indicator acts as a decision‑support layer, not a strategy, signal service, or automated system.

1. Target Users
Included Users
• Discretionary traders (stocks, indices, crypto)
• Day traders, swing traders, position traders
• Options traders using directional bias
• Traders who already use RSI, EMAs, price action, or support/resistance
Explicitly Excluded Users
• News/event‑driven traders
• Fully automated strategy seekers
• High‑frequency scalpers
• Users looking for guaranteed buy/sell alerts

2. Platform & Distribution Strategy
Phase 1 (Mandatory)
• TradingView native indicator (Pine Script)
• Applied to any symbol already loaded on the chart
• No external website required
Explicitly Out of Scope (Phase 1)
• Standalone website or charting platform
• Stock/crypto selection or recommendations
• Scanners or watchlist ranking
• Broker integration
• Automation or bots

3. Core Product Philosophy
What This Indicator IS
• A Market Readiness & Trade Permission tool
• Always informative (never silent)
• Gradual and probabilistic, not binary
• Visual‑first, low cognitive load
What This Indicator IS NOT
• Not a signal generator
• Not a strategy
• Not an AI predictor
• Not an optimizer or backtester
• Not a trade execution system

4. Key Problem Being Solved
Most traders fail not because of bad entries, but because they: - Trade during chop - Trade late in exhausted trends - Trade when risk asymmetry is poor - Overtrade due to lack of context
Existing indicators answer what is happening.
This product answers whether acting is sensible right now.

5. High‑Level Functional Overview
The indicator evaluates internal behavior of the active chart and produces:
6. Primary Market Label (human‑readable)
7. Secondary Readiness Score (numeric)
8. Supporting visual context (backgrounds, small meters)
No buy/sell arrows are generated.

9. Output Design (User‑Facing)
8.1 Primary Label (Mandatory)
One of three mutually exclusive states:
• 🟢 TRADE‑FAVORABLE
• 🟡 MIXED CONDITIONS
• 🔴 RISK ZONE
This label is the main decision anchor for the user.

8.2 Secondary Score (Mandatory)
• Numeric score from 0 to 100
• Purpose: indicate degree, not permission
Example interpretation: - 70–100 → Favorable environment - 40–69 → Mixed / selective - 0–39 → Risk‑dominant environment
Score must: - Update smoothly (no erratic jumps) - Never be permanently stuck at extremes

8.3 Visual Hierarchy Rules

1. Label = highest visual priority
2. Score = secondary priority
3. Supporting visuals = subtle, optional
No more than 3 major visual elements at once.

4. Internal Market Evaluation Model (Abstract)
IMPORTANT
The following are conceptual behaviors, not exposed indicators.
The user must never see RSI, MACD, EMA, ATR lines.

9.1 Market Dimensions Evaluated
The engine evaluates four independent but interacting dimensions:

1. Directional Pressure
Measures net price progress vs oscillation
2. Volatility Regime
Detects expansion vs compression environments
3. Trend Energy / Participation
Identifies continuation vs decay
4. Risk Asymmetry
Compares potential upside vs downside at current location
Each dimension contributes proportionally to the final score.

5. Behavioral Design Rules (Critical)
To avoid the past “no‑trade” problem:
• No hard blocking conditions
• No all‑conditions‑must‑pass logic
• No binary gating
• Overlapping states are allowed
The system must always output a state, even on poor days.

6. Timeframe & Symbol Handling
• Indicator reads only the active chart
• No normalization across symbols
• Each symbol is evaluated relative to its own behavior
• Works on all timeframes (1m → daily)

7. Performance & Responsiveness
• Output should not flip excessively
• Labels should favor stability over reactivity
• Score should change faster than label

8. User Controls (Phase 1 – Minimal)
• Enable / disable background shading
• Enable / disable score display
No advanced tuning or parameter optimization.

9. Compliance & Risk Positioning
• No profit guarantees
• No win‑rate claims
• Clear disclaimer: decision support only
• Not designed for news/event trading

10. Success Criteria (Phase 1)
The product is successful if: - Traders understand it within 30 seconds - It helps users avoid bad trades - It reduces overtrading behavior - Users apply it alongside existing tools

11. Explicit Non‑Goals (Locked)
The product will never: - Pick stocks - Generate trade signals - Predict price - Replace trader judgment - Compete with TradingView

12. Future Expansion (Not in Scope)
• Scanners / watchlist ranking
• Multi‑symbol dashboards
• Bot integration (IBKR or others)
• AI optimization or backtesting
These require separate validation.

13. Status
Document Status: Frozen – Phase 1
Changes require explicit discussion and revision
