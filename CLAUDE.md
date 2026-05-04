# CLAUDE.md — ICC Pine Script Indicator

## About
TradingView Pine Script v6 indicator implementing the ICC (Indication, Correction, Continuation) strategy inspired by Trades by Sci (Umar Ashraf). Detects swing structure, identifies ICC phases, and generates entry signals with risk management levels.

## Tech stack
- **Language:** Pine Script v6 (TradingView)
- **Single file:** `ICC_Indicator.pine`

## Key concepts
- **Indication:** Aggressive BOS/CHoCH swing break (1H/4H bias)
- **Correction:** Counter-trend pullback into 50-79% Fibonacci AOI zone
- **Continuation:** Price resumes indication direction, breaks back beyond the level (ENTRY)

## Pine Script conventions
- Use `var` for persistent state across bars
- Use `ta.pivothigh()`/`ta.pivotlow()` for non-repainting swing detection
- Actual swing bar = `bar_index - pivotLen` (lagged confirmation)
- One `request.security()` call max for MTF (avoid repainting)
- All drawing objects capped to prevent memory overflow
- `alertcondition()` for static alerts, `alert()` for dynamic messages

## Testing
1. Load in TradingView Pine Editor
2. Apply to 15M EURUSD or SPY chart
3. Use Bar Replay to verify non-repainting
4. Confirm swing labels match visible pivots
5. Walk through known ICC setups from Trades by Sci videos