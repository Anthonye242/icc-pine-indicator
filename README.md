# ICC Pine Script Indicator

A TradingView Pine Script v6 indicator implementing the **ICC (Indication, Correction, Continuation)** strategy inspired by [Trades by Sci](https://www.youtube.com/@TradesBySci) (Umar Ashraf).

## What is ICC?

ICC is a three-phase price action framework that identifies high-probability trend continuation entries:

| Phase | What Happens | Action |
|-------|-------------|--------|
| **Indication** | Price aggressively breaks a swing high/low (BOS or CHoCH) | Mark bias — do NOT trade |
| **Correction** | Counter-trend pullback into 50–79% Fibonacci zone (AOI) | Monitor — do NOT trade |
| **Continuation** | Price resumes and breaks back beyond the indication level | **ENTER the trade** |

## Features

- **Swing Detection** — Non-repainting pivot highs/lows with configurable lookback
- **Market Structure** — Automatic HH/HL/LH/LL classification, BOS/CHoCH detection
- **ICC State Machine** — Tracks all three phases with visual feedback
- **AOI Zones** — Fibonacci-based Area of Interest (50-79% retracement)
- **Risk Management** — Auto-calculated Entry, Stop Loss, TP1 (1.5R), TP2 (3R)
- **Multi-Timeframe** — Optional HTF trend confirmation filter
- **Session Filter** — Trade only during specified market hours
- **Volume Filter** — Optional volume confirmation on indication moves
- **Info Dashboard** — Real-time table showing phase, bias, correction depth
- **Alerts** — All phase transitions + entry signals with full level details
- **Phase Background** — Optional color overlay showing current ICC phase

## Installation

1. Open TradingView → Pine Editor
2. Copy the contents of `ICC_Indicator.pine`
3. Click "Add to Chart"
4. Recommended: Apply to 15M chart with 1H/4H HTF confirmation enabled

## Recommended Settings

| Instrument | Pivot Len | Min Strength | Fib Zone | Session |
|-----------|-----------|--------------|----------|---------|
| Forex (EURUSD) | 3 | 1.5 ATR | 50-79% | 0200-1700 |
| US Stocks (SPY) | 3 | 1.5 ATR | 50-79% | 0930-1600 |
| Crypto (BTCUSD) | 5 | 2.0 ATR | 50-79% | 24h |

## Alerts

Set up alerts for any of these conditions:
- Indication Detected (new BOS/CHoCH)
- Correction Started
- Price Entered AOI Zone
- **Continuation Signal (Long/Short)** ← main entry alert
- Setup Invalidated
- BOS / CHoCH Detected

## Non-Repainting

All signals are confirmed `pivotLen` bars after the swing forms. Entry signals fire on bar close only. No future data is used.

## Credits

- Strategy concept: [Trades by Sci](https://www.youtube.com/@TradesBySci) (Umar Ashraf)
- Built by: [TropiSync](https://github.com/TropiSync)