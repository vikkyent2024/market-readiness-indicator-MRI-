# Indicator Output UX Specification

## Product: Market Readiness Indicator (MRI)
**Platform:** TradingView (Pine Script – Invite-Only)

---

## 1. Purpose of This Document

This document defines the **exact user-facing output behavior** of the Market Readiness Indicator.

It exists to:
- Prevent visual clutter and confusion
- Enforce clarity and simplicity
- Ensure the indicator delivers value in <30 seconds
- Avoid LuxAlgo-style overload
- Provide precise instructions for implementation (human or AI)

This document covers **WHAT the user sees**, not internal logic.

---

## 2. Core UX Principles (Non-Negotiable)

1. **Clarity over completeness**
2. **Labels first, numbers second**
3. **Never overwhelm the chart**
4. **Stable signals > reactive noise**
5. **Explain the environment, not the trade**

If a visual element does not directly support these principles → it must be removed.

---

## 3. Primary Output: Market Readiness Label

### 3.1 Label Set (Locked)

Exactly **one** label must be active at any time:

- 🟢 **TRADE-FAVORABLE**
- 🟡 **MIXED CONDITIONS**
- 🔴 **RISK ZONE**

No additional labels, sub-labels, or text variants are allowed in Phase 1.

---

### 3.2 Label Behavior Rules

- Label must **always be visible**
- Label must not flicker or rapidly alternate
- Label changes should require **meaningful condition shifts**
- Label is **stickier** than the numeric score (hysteresis)

Label priority:
> Label > Score > Background visuals

---

### 3.3 Label Placement

Recommended placement:
- **Top-right or top-center of chart**
- Non-overlapping with candles
- Consistent position across symbols and timeframes

---

## 4. Secondary Output: Market Readiness Score

### 4.1 Score Definition

- Numeric score range: **0 to 100**
- Integer or one decimal max
- Always displayed alongside label

---

### 4.2 Score Interpretation Bands

| Score Range | Interpretation |
|------------|---------------|
| 70–100 | Favorable environment |
| 40–69 | Mixed / selective |
| 0–39 | Risk-dominant |

These bands are **interpretive only** and must not be shown explicitly on the chart.

---

### 4.3 Score Behavior Rules

- Score may update more frequently than label
- Score must change **smoothly**, not jump erratically
- Score must never be permanently stuck at 0 or 100
- Score should reflect **degree**, not permission

---

## 5. Supporting Visuals (Optional, Minimal)

### 5.1 Background Shading (Optional)

If enabled:
- Subtle, low-opacity background tint
- Color must match active label
- Must not obscure candles or other indicators

Opacity guidance:
- Maximum 5–8%

---

### 5.2 Trend Health / Context Indicator (Optional)

If included:
- Small ribbon or meter
- Placed below label or at chart edge
- No numbers, no text
- Uses muted color gradient only

This element must NEVER compete with the primary label.

---

## 6. Color System (Locked)

### 6.1 Primary Colors

- **Green:** Favorable (not neon, not bright)
- **Yellow / Amber:** Mixed
- **Red:** Risk (not aggressive, avoid panic red)

Colors must:
- Be consistent across all visuals
- Be readable on dark and light chart themes

---

## 7. Update & Responsiveness Rules

### 7.1 Temporal Behavior

- Label updates should be **slower and deliberate**
- Score updates can be **faster and responsive**

This ensures:
- Stability in decision-making
- No “signal chasing” behavior

---

## 8. Alerts UX Specification

### 8.1 Allowed Alert Types

Alerts may trigger on:
- Label change (e.g., MIXED → TRADE-FAVORABLE)
- Score crossing user-defined thresholds

---

### 8.2 Alert Language Constraints

Alerts must:
- Avoid BUY / SELL wording
- Use neutral phrasing

Examples:
- “Market condition improved: Trade-Favorable”
- “Risk environment detected”

---

## 9. User Configuration Controls (Minimal)

Allowed toggles:
- Show / hide background shading
- Show / hide numeric score

No parameter tuning, optimization sliders, or advanced settings in Phase 1.

---

## 10. Accessibility & Cognitive Load

- Must be interpretable at a glance
- Must not require reading documentation during trading
- Must work equally well on:
  - 5m chart
  - 1h chart
  - Daily chart

---

## 11. UX Anti-Patterns (Explicitly Forbidden)

- Buy/Sell arrows
- Multiple conflicting labels
- Indicator lines over price
- Pop-up text blocks
- Flashing or animated visuals
- Strategy-like elements

---

## 12. Validation Checklist (Before Release)

Before finalizing:

- Can a new user explain the indicator in one sentence?
- Is the label readable within 2 seconds?
- Does the chart still feel clean?
- Does it add value even when not trading?

If any answer is NO → revise.

---

## 13. Status

**Document Status:** Locked – Phase 1 UX  
**Changes require explicit approval**

---

*End of Indicator Output UX Specification*

