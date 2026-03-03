# Options Greeks Reference

Comprehensive reference for the five major Greeks, their interactions, and application to position sizing.

---

## Delta

Delta measures the expected change in option price for a $1 change in the underlying asset.

### Delta Position Table

| Position | Delta Range | Interpretation |
|----------|------------|----------------|
| Long Call | 0 to +1.0 | Positive delta; profits when stock rises |
| Short Call | 0 to -1.0 | Negative delta; profits when stock falls |
| Long Put | -1.0 to 0 | Negative delta; profits when stock falls |
| Short Put | 0 to +1.0 | Positive delta; profits when stock rises |
| Long Stock | +1.0 per share | Baseline directional exposure |
| Short Stock | -1.0 per share | Inverse directional exposure |

### Delta Key Values

- **ATM options** have delta near +/-0.50
- **Deep ITM options** have delta approaching +/-1.0 (behave like stock)
- **Far OTM options** have delta approaching 0 (minimal price sensitivity)
- **Delta as probability proxy** -- An option with 0.30 delta has roughly a 30% chance of expiring in-the-money (this is an approximation, not exact)

### Delta Uses

- **Hedge ratio** -- To delta-hedge 100 shares of long stock (+100 delta), buy 2 ATM puts (-50 delta each) for a delta-neutral position.
- **Portfolio delta** -- Sum the deltas of all positions to find net directional exposure. Express as "equivalent shares" of the underlying.
- **Delta-neutral strategies** -- Straddles, strangles, and iron condors start near delta-neutral but shift as the underlying moves.

---

## Gamma

Gamma measures the rate of change of delta for a $1 change in the underlying. It tells you how fast your directional exposure is changing.

### Gamma: Highest and Lowest

- **Highest gamma** -- ATM options near expiration. Delta changes rapidly with small price moves.
- **Lowest gamma** -- Deep ITM/OTM options and long-dated options. Delta is relatively stable.

### Long Gamma vs Short Gamma

| Exposure | Meaning | Risk Profile |
|----------|---------|-------------|
| Long Gamma | Delta moves in your favor as stock moves | Benefits from large moves; long options positions |
| Short Gamma | Delta moves against you as stock moves | Benefits from stability; short options positions |

### Gamma Risk

- **Gamma risk accelerates near expiration** -- In the final days before expiration, ATM options have extremely high gamma. A $1 move can flip an option from OTM to ITM (or vice versa), causing dramatic P&L swings.
- **Pin risk** -- When the underlying is near a strike at expiration, gamma is at its peak. Short gamma positions face the highest risk of adverse moves.
- **Gamma scalping** -- Long gamma traders can profit by delta-hedging: as the stock moves, they buy low and sell high to capture the convexity of their long options position.
- **Short gamma and gap risk** -- Short gamma positions are exposed to overnight gaps. A stock that gaps 10% after earnings can cause losses far exceeding what theta collected.

---

## Theta

Theta measures the daily time decay of an option's value. It represents the cost of holding a long option or the income from holding a short option.

### Theta: Always Negative for Buyers, Positive for Sellers

- **Long options** -- Theta is negative. The option loses value each day, all else equal.
- **Short options** -- Theta is positive. The seller collects time decay as income.

### Theta Acceleration

Theta decay is not linear. It follows a curve that accelerates as expiration approaches:

- **60+ DTE** -- Slow decay. Theta is relatively small. Long-dated options retain time value well.
- **30-60 DTE** -- Moderate decay. The "sweet spot" for selling premium with reasonable time to be right.
- **14-30 DTE** -- Accelerating decay. This is where theta sellers earn the majority of their income.
- **0-14 DTE** -- Rapid decay. ATM options lose value quickly. Short-dated premium selling is profitable but carries high gamma risk.

### Theta and ATM vs OTM

- **ATM options** have the highest absolute theta. They contain the most extrinsic (time) value.
- **OTM options** have lower absolute theta but higher theta relative to their price. A $0.50 option losing $0.05/day decays 10% per day.
- **ITM options** have lower theta because much of their value is intrinsic, which does not decay.

### Theta Rule of Thumb

An ATM option loses approximately 1/sqrt(DTE) of its value per day when expressed as a fraction of the total time value. In practical terms, the final third of the option's life accounts for roughly two-thirds of the total time value decay.

### Theta by Days to Expiration (DTE)

| DTE | Daily Decay Rate | Cumulative Decay | Notes |
|-----|-----------------|-----------------|-------|
| 90 | ~0.5% per day | Baseline | Slow decay; good for long options |
| 60 | ~0.7% per day | ~15% decayed | Still manageable for buyers |
| 45 | ~0.9% per day | ~25% decayed | Common entry for premium sellers |
| 30 | ~1.1% per day | ~40% decayed | Decay noticeably accelerating |
| 21 | ~1.4% per day | ~52% decayed | Recommended close/roll point |
| 14 | ~1.8% per day | ~65% decayed | Gamma risk rising significantly |
| 7 | ~2.8% per day | ~80% decayed | High gamma, rapid decay |
| 3 | ~5.0% per day | ~92% decayed | Extreme gamma risk |
| 1 | ~10%+ per day | ~98% decayed | Expiration day; binary outcomes |

---

## Vega

Vega measures the sensitivity of an option's price to a 1 percentage point change in implied volatility.

### Vega: Long and Short

| Exposure | Meaning | Profits When |
|----------|---------|-------------|
| Long Vega | Position benefits from IV increase | IV rises (buy straddles, buy options before events) |
| Short Vega | Position benefits from IV decrease | IV falls (sell straddles, sell options after events) |

### Vega and Strategy Selection

| IV Environment | IV Rank | Preferred Strategies | Rationale |
|---------------|---------|---------------------|-----------|
| Low IV | < 25% | Buy options, long straddles/strangles, debit spreads | Options are cheap; IV likely to expand |
| Below Average IV | 25-50% | Debit spreads, calendars, long options | Slightly favor buying strategies |
| Above Average IV | 50-75% | Credit spreads, iron condors, short strangles | Slightly favor selling strategies |
| High IV | > 75% | Sell premium aggressively, iron condors, short straddles | Options are expensive; IV likely to contract |

### Vega Key Properties

- **Longer-dated options have higher vega** -- A 1-point IV change affects a 90 DTE option more than a 7 DTE option.
- **ATM options have the highest vega** -- They are most sensitive to volatility changes.
- **Vega decreases as expiration approaches** -- Near-expiration options are relatively insensitive to IV changes (theta and gamma dominate).
- **Vega is additive across legs** -- For multi-leg strategies, sum the vega of each leg to find net vega exposure.

---

## Rho

Rho measures the sensitivity of an option's price to a 1 percentage point change in the risk-free interest rate.

### Rho Key Properties

- **Calls have positive rho** -- Call prices increase when interest rates rise (higher cost of carry favors calls over stock ownership).
- **Puts have negative rho** -- Put prices decrease when interest rates rise.
- **Rho is typically small** -- For short-dated options, rho is negligible. It becomes more significant for LEAPS (options with 1-2+ years to expiration).
- **Rising rate environments** -- When rates are changing rapidly, rho can contribute meaningfully to LEAPS pricing. A 1% rate increase on a 2-year LEAPS call could add $0.50-$1.00+ in value per contract.

---

## Combined Greeks Profiles: Common Strategy Greeks

Understanding how the Greeks interact within a strategy is critical. Below are the typical Greeks profiles at initiation for common strategies:

| Strategy | Delta | Gamma | Theta | Vega | Risk Profile |
|----------|-------|-------|-------|------|-------------|
| Long Call | + | + | - | + | Bullish; benefits from move up and IV expansion |
| Long Put | - | + | - | + | Bearish; benefits from move down and IV expansion |
| Covered Call | + (reduced) | - | + | - | Mildly bullish; income focus; caps upside |
| Bull Call Spread | + | ~0 | ~0 | ~0 | Moderately bullish; defined risk; Greeks partially offset |
| Bear Put Spread | - | ~0 | ~0 | ~0 | Moderately bearish; defined risk; Greeks partially offset |
| Long Straddle | ~0 | + | - | + | Neutral; profits from large move in either direction |
| Short Straddle | ~0 | - | + | - | Neutral; profits from stability and time decay |
| Iron Condor | ~0 | - | + | - | Neutral; defined risk; profits from range-bound action |
| Calendar Spread | ~0 | - (near) / + (far) | + | + | Neutral; profits from time decay differential and IV rise |
| Iron Butterfly | ~0 | - | + | - | Neutral; max profit if underlying pins at center strike |
| Jade Lizard | + (slight) | - | + | - | Bullish-neutral; no upside risk if structured correctly |

---

## Position Sizing with Greeks

### Delta-Based Sizing

- **Target portfolio delta** -- Express your desired directional exposure as a number of equivalent shares (delta dollars).
- **Example** -- If you want the equivalent of 500 shares of exposure and each option has 0.50 delta, buy 10 contracts (10 x 100 x 0.50 = 500 delta).
- **Delta-dollar exposure** -- Multiply your net delta by the stock price. If you have 500 delta on a $100 stock, your delta-dollar exposure is $50,000.
- **Maintain balance** -- Keep total portfolio delta within your risk tolerance. Diversify across uncorrelated underlyings to avoid concentrated directional bets.

### Theta-Based Sizing

- **Daily theta budget** -- Determine how much time decay you are comfortable paying (long options) or collecting (short options) per day.
- **Example** -- If your daily theta budget is -$50 (willing to pay $50/day in decay), and each long straddle has -$10 theta, you can hold 5 straddles.
- **Theta as income target** -- Premium sellers often target a daily theta collection relative to portfolio size (e.g., 0.05-0.10% of portfolio per day).

### Vega-Based Risk

- **Portfolio vega exposure** -- Sum the vega across all positions. This tells you how much your portfolio will gain or lose for each 1-point move in IV.
- **Vega risk limit** -- Set a maximum portfolio vega relative to account size. A common guideline is that a 5-point IV move should not impact the portfolio by more than 2-3%.
- **Example** -- If portfolio vega is $2,000 and IV drops 5 points, the portfolio loses $10,000. Ensure this is within your risk tolerance.
- **Hedging vega** -- If you are short too much vega, buy some long-dated options or VIX calls to offset. If long too much vega, sell some near-term premium.
