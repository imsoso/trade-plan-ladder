# Trade Plan Ladder 🪜

> **Turn a written trade plan into a live chart. No signals — just your plan, drawn.**

**TradingView script:** https://cn.tradingview.com/script/mHzKfd7Z/

A Pine Script v6 indicator for TradingView that takes **your own trade plan** — entry ladder, confirmation trigger, invalidation, targets — draws it on the chart, computes risk/reward and position size for each tranche, and fires price alerts with the computed quantity.

Most indicators tell you *when to buy*. This one assumes you already did the analysis: it enforces the plan.

## Features

- 🪜 **Ladder entries** — A1/A2 limit zones + B confirmation trigger (N consecutive closes above trigger = stabilization) + C trend-continuation pullback
- 📐 **Two level modes** — `Relative %` (anchored to yesterday's close; works out-of-the-box on any symbol, re-anchors daily like pivot points) or `Absolute` (exact prices for a fixed plan)
- 🛡 **Two-layer protection** — invalidation on *daily close* vs intrabar *hard stop*: wicks and closes are different things
- 🧮 **Position sizing** — capital × risk% ÷ stop distance, split across tranches (A1 40% / A2 40% / B-C 20% by default)
- 📊 **R:R per tranche** in a trade-card table that never stretches the price scale
- 📏 **Dual auto trendlines** — external line (major top → next lower pivot, strict wick extremes) + internal line (time-windowed least-squares regression over recent swing highs)
- 🎯 **Band-filtered drawing** — far levels auto-hide; your price scale stays clean
- 🔔 **7 alert conditions** + one dynamic `alert()` stream with quantity included

## Install

**Option A — direct:** open the script on TradingView and add it to your chart: https://cn.tradingview.com/script/mHzKfd7Z/

**Option B — from source:**

1. Open TradingView → **Pine Editor**
2. Paste the contents of [`Trade-Plan-Ladder-v0.2.1-public.pine`](./Trade-Plan-Ladder-v0.2.1-public.pine)
3. **Save** → **Add to chart**
4. (Optional) Chart settings → Scales → *Scale price chart only* — drawings will never affect autoscaling

## Quick start

1. Set `Mode` to `Relative %` for instant levels on any symbol, or `Absolute` + your exact prices
2. Enter capital and max risk % — the table shows qty/value/RR per tranche
3. Place limit orders at your venue, then create **one** alert with condition *“Any alert() function call”*

Works on any linear market: crypto spot, stocks, ETFs, forex. Recommended timeframe: 1h and above (B confirmation counts chart-TF closes).

## Disclaimer

Educational tool. **Not financial advice.** Places no orders. Quantity is full-size math — always verify against your own account before trading.

## License

[MIT](./LICENSE)

---

## 中文说明

**Trade Plan Ladder（交易计划阶梯）** —— 把写在纸上的交易计划画到图上的 TradingView 指标（Pine Script v6）。

多数指标告诉你"何时买"；这个工具假设你已经做完分析，它负责**执行纪律**：把你的计划——限价阶梯（A1/A2）、确认触发（B，连续 N 根收盘收回=企稳）、趋势回踩（C）、日收盘失效线、盘中硬止损、供给区目标——全部画线、算好每笔的盈亏比与数量、到点提醒（提醒消息带计算数量）。

**关键位双模式**：`Relative %`（相对百分比，锚定昨收盘，任何品种开箱即用，类似枢轴点每日重锚）/ `Absolute`（绝对价格，固定计划用）。另附双自动趋势线（外线=大顶连次高针顶；内线=近期波段高点时间窗回归）与带宽过滤画线（远处位自动隐藏，不拉爆纵轴）。

适用于任何线性计价市场：加密现货、股票、ETF、外汇。建议 1h 及以上周期。**非策略脚本，不下单；仅供研究，非投资建议；数量为满额计算，下单前自行核对。**
