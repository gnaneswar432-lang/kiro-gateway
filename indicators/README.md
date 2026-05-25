# BB(20, 1.5) + Candlestick — Pine Script v6 Indicator

Trading indicator built for the **Nifty 50 — 100 Days Trading Challenge** strategy.
Written in **Pine Script v6** (TradingView's latest, released 2025).

> *"Bollinger Band (20, 1.5) + Candlestick"* — One trade a day, 1:2 R:R, 5-minute Nifty Futures, intraday only.

## Files

| File | Purpose |
|------|---------|
| `BB_Candlestick_Strategy.pine` | The indicator. Plots BB(20, 1.5), detects bullish/bearish reversal candles at the bands, and fires Buy/Sell signals with auto SL & 1:2 Target. |

## What it does

- **BUY** when a bullish reversal candle (Hammer, Bullish Engulfing, Piercing, Bullish Harami, Bullish Marubozu) forms touching/near the **lower** Bollinger Band.
- **SELL** when a bearish reversal candle (Shooting Star, Bearish Engulfing, Dark Cloud Cover, Bearish Harami, Bearish Marubozu) forms touching/near the **upper** Bollinger Band.
- Auto-plots **Entry**, **Stoploss** (signal candle low/high) and **Target** (default 1:2 R:R).
- Enforces **one signal per trading day** (configurable).
- Configurable intraday **session window** (default `0915-1500` IST).
- Native **TradingView alerts** for Buy and Sell.

## How to install on TradingView

1. Open TradingView → any Nifty Futures chart on the **5-minute** timeframe.
2. Press `Pine Editor` (bottom panel) → click *Open* → *New Indicator* → paste the contents of `BB_Candlestick_Strategy.pine`.
3. Click **Save** → **Add to chart**.
4. Right-click any signal → *Add alert* → choose **BUY Signal** or **SELL Signal**.

## If the bands appear in a separate pane below the candles

The script declares `overlay = true`, so it should sit **on top of the price chart**. If TradingView accidentally drops it into its own sub-panel, fix it once:

- **Right-click the indicator's name** (top-left of the chart) → **Move to** → **Existing Pane Above**, OR
- Drag the bottom edge of the indicator panel up onto the candle panel until they merge.

Once merged, the BB lines will hug the candles exactly as in the strategy images.

## Recommended settings (per challenge rules)

| Input | Value |
|-------|-------|
| BB Length | 20 |
| BB StdDev | 1.5 |
| Risk:Reward | 2.0 |
| One signal per day | **OFF** by default (shows every trigger). Turn **ON** when running the strict 100-day challenge. |
| Session | 0915-1500 (or 0925-1500 to skip opening noise) |
| Touch tolerance | 0.10 % |

## Trader's checklist before taking a signal

1. Is the day **range-bound** (bands roughly parallel)? Strong trending days = skip.
2. Is the signal candle's **wick clearly testing the band**, not just floating?
3. Is there a confluence — round number, prior swing, VWAP — within a few ticks of entry?
4. Confirm SL distance (in points) is acceptable for your option-premium risk via delta.

## Disclaimer

This is educational tooling. The challenge rules in the source images are paraphrased for code; trade your own plan and size accordingly.
