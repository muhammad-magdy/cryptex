# ◈ CRYPTEX — AI Crypto Early Mover Advisor

An AI-powered crypto day trading dashboard that scans **300+ Binance pairs** every 90 seconds to detect volume spikes and early movers **before they appear on the gainers list**.

🌐 **Live:** https://muhammad-magdy.github.io/cryptex

---

## Features

### ⚡ Early Mover Scanner
- Scans all Binance USDT pairs every 90 seconds
- Detects coins with 2x–10x unusual volume before the price move
- Falls back to CoinGecko automatically if Binance is geo-blocked
- Filters by minimum volume spike, % change, and signal type

### ⭐ Trade Quality Score (A+ → F)
Every coin is graded using a weighted scoring system across six factors:
| Factor | What it measures |
|--------|-----------------|
| Volume Spike | Abnormal trading activity vs. median |
| Day Position | Where price sits in today's range (avoids chasing tops) |
| Momentum | RSI-style score — catches oversold bounces and healthy trends |
| % Change | Rewards real moves, penalises parabolic pumps |
| Liquidity | 24h USD volume — filters manipulation risk |
| Volatility | Day range — rewards tradeable, penalises wild swings |

Click any grade badge to see the full point-by-point breakdown.

### 🤖 AI Analysis (Claude)
- **Per-coin:** Entry / Target / Stop Loss / Risk:Reward / Timeframe / Confidence
- **Full scan:** Market sentiment, top picks, fake pump warnings, best trading window
- News from CryptoCompare is factored into every prediction

### 💼 Paper Trading
Full paper trade lifecycle with zero real money:

**Opening a trade**
- Choose amount and confirm entry
- AI suggests an exit strategy based on coin metrics at entry time

**Smart Exit Strategy**
Each trade gets one of two strategies (AI-suggested, user-overridable):

| Strategy | When suggested | Auto-exit rules |
|----------|---------------|-----------------|
| 🌊 **Ride the Wave** | A+ grade · >$50M volume · >30x spike · <60% day pos | Trail 5% from peak (once +5% profit reached) |
| 🛡️ **Bank Profits** | Everything else | Exit when day pos ≥ 85% + profit > 10%, or grade drops to D/F |

**Universal rule (both strategies):** Recommended stop loss from entry always triggers auto-close first.

**Auto-close system**
- Toggle per trade (default: ON)
- Fires on every 90-second price refresh
- Saves exit reason to trade history
- Shows a dismissable notification banner when triggered

**Live trade cards show:**
- Entry price · current price · peak price + peak P&L%
- "Should I sell?" advice: `HOLD` / `TIGHTEN STOP` / `CLOSE NOW`
- Live metrics: current grade, vol spike, momentum, day position
- Exit levels: stop loss (% from now) + peak trail or bank trigger
- Duration since entry

### 📓 Trading Journal
Full history with performance analytics:

**Performance Summary**
- Total trades · win rate · total P&L · avg win · avg loss
- Best and worst trade
- Breakdown **by strategy** (win rate + avg P&L per strategy)
- Breakdown **by entry grade** (avg P&L per grade)
- Breakdown **by exit reason** (stop loss / peak confirmed / day pos / grade drop / manual)

**History filters:** All · 🌊 Ride · 🛡️ Bank · ✅ Wins · ❌ Losses · 🤖 Auto · ✋ Manual

**Sort:** Newest first · Oldest first · Biggest profit

**12-column table (horizontally scrollable):**
`SYMBOL` · `STG` · `ENTRY GRADE` · `DAY POS` · `ENTRY` · `EXIT` · `PEAK` · `P&L €` · `P&L %` · `DURATION` · `REASON` · `BY`

### 📰 News & Sentiment
- Live crypto news from CryptoCompare (sentiment-tagged)
- Fear & Greed Index from alternative.me
- Both factored into AI analysis

---

## Data Sources
| Source | Data |
|--------|------|
| Binance REST API | 300+ pairs · price · volume · high/low · 90s refresh |
| CoinGecko API | Fallback price data when Binance is geo-blocked |
| alternative.me | Fear & Greed Index |
| CryptoCompare | Latest crypto news with sentiment |
| Claude AI (Sonnet) | Trade plans · market scan · signal analysis |

---

## Tech Stack
- Single `index.html` — no build step, no dependencies
- React 18 + JSX via Babel standalone (CDN)
- All state in `useState` / `useEffect`
- Trade history persisted in `localStorage` (`cryptex_trades_v1`)

---

## ⚠️ Disclaimer
For educational purposes only. Not financial advice. Crypto day trading is extremely high risk. Always use stop losses. Never risk more than you can afford to lose.
