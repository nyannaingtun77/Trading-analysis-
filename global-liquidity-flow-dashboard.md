# Global Liquidity Flow Dashboard Prompt

## Purpose
Use this prompt when crypto, gold, bonds, or equities are falling and we want to identify where capital/liquidity is actually moving.

Do **not** assume that a decline in market capitalization equals the same amount of cash leaving the asset. Distinguish between:
1. Real cash/capital rotation
2. Cash parking
3. New debt/primary issuance absorbing capital
4. Deleveraging / margin liquidation / debt repayment that destroys balance-sheet liquidity
5. Price revaluation without equivalent cash outflow

## Required live-data checks
Always use the latest available data and show the exact observation/trading date. Prefer official or primary sources and verify current values rather than relying on stale search snippets.

### A. Crypto risk and crypto cash parking
- BTC price and 24h / 7d change
- ETH price and 24h / 7d change
- Total crypto market cap if available
- U.S. spot BTC ETF daily net flow
- U.S. spot ETH ETF daily net flow
- Total stablecoin market cap
- Stablecoin 1d / 7d / 30d change
- USDT and USDC supply changes

Preferred sources: Farside / SoSoValue for ETF flows, DefiLlama for stablecoin supply, reliable market-data sources for prices.

### B. USD / cash / cash-equivalent demand
- DXY current level and daily change
- U.S. money-market fund total assets and latest weekly change
- 3-month / 6-month T-bill yields when relevant

Preferred sources: Reuters / ICE or reliable market data for DXY, Investment Company Institute (ICI) for money-market funds, U.S. Treasury / FRED for bills.

### C. Federal Reserve liquidity plumbing
Track:
- Fed total assets: WALCL
- Reserve balances: WRESBAL or Wednesday-level reserve balance series
- Treasury General Account: WDTGAL / TGA
- Overnight Reverse Repo: RRPONTSYD

Calculate a simple liquidity proxy when data dates are compatible:
**Fed Net Liquidity Proxy = Fed Total Assets - TGA - ON RRP**

Clearly label this as a simplified market proxy, not an official Fed measure.

Interpretation rules:
- TGA rising = generally drains reserves / private-system liquidity
- TGA falling = generally releases liquidity
- RRP falling = can release cash into the private system, but if RRP is already near zero the remaining release buffer is small
- Reserve balances falling = tighter banking-system liquidity
- Fed assets falling = QT / balance-sheet contraction pressure, all else equal

### D. Rates and bond market
Track:
- U.S. 2Y yield
- U.S. 10Y yield
- U.S. 30Y yield
- 2s10s curve when useful
- Treasury auction size/demand when a major auction is occurring
- MOVE index / bond volatility
- Term premium when available

Important interpretation:
- Yield up = existing bond price down. Do not call this a bond-price inflow.
- Strong demand at new Treasury/corporate issuance can still absorb large amounts of capital even while secondary-market bond prices fall.

### E. Commodities / inflation hedge
Track:
- Gold
- Brent crude
- WTI crude
- Natural gas if it is materially moving

Separate price moves caused mainly by supply shocks from broad liquidity-driven moves.

### F. Equity rotation
Track:
- S&P 500
- Nasdaq
- Russell 2000
- Major sector leadership
- Specifically note Energy, Consumer Staples, Utilities and other defensive sectors when they outperform during risk-off periods
- Credit spreads if reliable current data are available

### G. Volatility / stress
Track:
- VIX
- MOVE

Interpret divergence:
- Low VIX + high MOVE = equity market may still look calm while bond-market stress is elevated
- Rising VIX + rising MOVE = broader cross-asset stress

## Required output format

### 1. Liquidity Dashboard
Create a compact table:
| Indicator | Latest | Change | Direction | What it means | Data date/source |

### 2. Where is the money/liquidity going?
Rank the destinations with confidence:
- USD / cash / cash equivalents
- Money-market funds / T-bills
- Stablecoins
- Oil / energy
- Defensive equities
- Treasuries / new debt issuance
- Gold
- Other obvious destination
- Deleveraging / debt repayment / margin liquidation (liquidity destruction)

Use High / Medium / Low confidence and give evidence for each.

### 3. Market regime diagnosis
Choose one or more:
- Risk-on rotation
- Risk-off rotation
- Cash/liquidity scramble
- Inflation shock
- Bond/fiscal stress
- Deleveraging / liquidity destruction
- Crypto-specific risk reduction

### 4. Crypto implication
Explain what the current macro/liquidity setup means for crypto **without issuing a buy/sell instruction**. State which signals would indicate liquidity is returning, such as:
- DXY weakening
- Treasury yields easing
- MOVE falling
- TGA declining or reserve balances improving
- Stablecoin supply expanding
- BTC/ETH ETF flows turning positive
- Broader equity breadth improving

## Accuracy rules
- Use the latest live/current source available.
- Show exact dates for data that update weekly rather than pretending they are real-time.
- If the latest weekly Fed or ICI release has not yet been published, explicitly say so and use the prior observation.
- Cross-check unusual values with a second source when possible.
- Never equate market-cap loss with identical cash outflow.
- Clearly distinguish observed data from interpretation.
- Do not invent flows when only price movement is known.
