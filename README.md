# @foundationalresearch/optionsderivatives

[![npm version](https://img.shields.io/npm/v/@foundationalresearch/optionsderivatives.svg)](https://www.npmjs.com/package/@foundationalresearch/optionsderivatives)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**A standalone AI skill for options and derivatives analysis.** Provides structured methodology for options pricing, Greeks analysis, strategy evaluation, hedging, and volatility trading. Works with Claude Code, Cursor, Codex, and any LLM-powered coding agent that supports skill files.

---

## What Is This?

This package contains a `SKILL.md` file and a `references/` directory that give AI agents deep expertise in options and derivatives analysis. When an agent loads this skill, it gains a rigorous 6-step framework for evaluating any options trade, from simple covered calls to complex multi-leg volatility strategies.

This is not a code library. It is a knowledge package -- structured instructions and reference data that make AI agents dramatically better at options analysis.

## 6-Step Methodology

The skill guides analysis through a complete workflow:

| Step | Focus | What It Covers |
|------|-------|----------------|
| **1. Understand the Objective** | Intent | Directional, income, hedging, volatility, or arbitrage |
| **2. Assess Market Context** | Environment | Price levels, IV, IV rank/percentile, IV skew, events, HV vs IV |
| **3. Greeks Analysis** | Risk Decomposition | Delta, Gamma, Theta, Vega, Rho -- individual and net position Greeks |
| **4. Strategy Selection** | Trade Structure | Match strategy to objective and market regime |
| **5. Position Sizing & Risk** | Risk Management | Max risk, position size, POP, break-evens, adjustments, exits |
| **6. Scenario Analysis** | Outcome Modeling | Price moves, IV changes, time decay, full P&L at expiration |

## Strategy Coverage

### Bullish Strategies

| Strategy | Max Gain | Max Loss | Best When |
|----------|----------|----------|-----------|
| Long Call | Unlimited | Premium paid | Strong bullish conviction, low IV |
| Bull Call Spread | Width - debit | Debit paid | Moderate bullish, high IV |
| Bull Put Spread | Credit received | Width - credit | Moderately bullish, high IV |
| Cash-Secured Put | Premium received | Strike - premium | Willing to buy stock, high IV |
| Covered Call | Premium + (strike - cost) | Cost basis - premium | Mildly bullish, income focus |
| Call Ratio Backspread | Unlimited upside | Varies | Strongly bullish, large move expected |
| Synthetic Long | Unlimited | Substantial | Bullish with less capital |

### Bearish Strategies

| Strategy | Max Gain | Max Loss | Best When |
|----------|----------|----------|-----------|
| Long Put | Strike - premium | Premium paid | Strong bearish conviction, low IV |
| Bear Put Spread | Width - debit | Debit paid | Moderate bearish, high IV |
| Bear Call Spread | Credit received | Width - credit | Moderately bearish, high IV |
| Put Ratio Backspread | Substantial downside | Varies | Strongly bearish, crash expected |
| Synthetic Short | Substantial | Unlimited | Bearish with defined entry |

### Neutral / Volatility Strategies

| Strategy | Max Gain | Max Loss | Best When |
|----------|----------|----------|-----------|
| Long Straddle | Unlimited | Both premiums | Expecting big move, low IV |
| Long Strangle | Unlimited | Both premiums | Expecting big move, cheaper entry |
| Short Straddle | Both premiums | Unlimited | Range-bound, high IV |
| Short Strangle | Both premiums | Unlimited | Range-bound, high IV |
| Iron Condor | Net credit | Width - credit | Range-bound, high IV, defined risk |
| Iron Butterfly | Net credit | Width - credit | Pinning at strike, high IV |
| Calendar Spread | Varies | Net debit | IV expansion, stable price |
| Diagonal Spread | Varies | Net debit | Directional bias + time decay |
| Jade Lizard | Credit | Put strike - credit | Bullish-neutral, high IV |
| Butterfly Spread | Width - debit | Debit paid | Pinning at center strike |

## Greeks Reference Included

The `references/greeks-reference.md` file provides comprehensive data for all five Greeks:

- **Delta** -- Position table, key values, hedge ratios, portfolio delta management
- **Gamma** -- Long vs short gamma exposure, gamma risk near expiration, gamma scalping
- **Theta** -- Decay acceleration curve, DTE-based decay rates, ATM vs OTM behavior
- **Vega** -- IV environment strategy selection, vega across expirations, hedging vega
- **Rho** -- Interest rate sensitivity for LEAPS and long-dated options
- **Combined Profiles** -- Greeks at initiation for 11 common strategies
- **Position Sizing** -- Delta-based, theta-based, and vega-based sizing frameworks

## Usage

### Claude Code

Add this skill to your project:

```bash
npm install @foundationalresearch/optionsderivatives
```

Add to your `.claude/settings.json`:

```json
{
  "skills": ["./node_modules/@foundationalresearch/optionsderivatives/SKILL.md"]
}
```

Or reference it in your `CLAUDE.md`:

```markdown
For options analysis, follow the methodology in node_modules/@foundationalresearch/optionsderivatives/SKILL.md
with reference data from node_modules/@foundationalresearch/optionsderivatives/references/greeks-reference.md
```

### Cursor

Add to `.cursor/rules`:

```
For options and derivatives analysis, follow the methodology defined in
node_modules/@foundationalresearch/optionsderivatives/SKILL.md

Greeks reference data is available at
node_modules/@foundationalresearch/optionsderivatives/references/greeks-reference.md
```

### Codex

Reference in your project instructions or system prompt:

```
When analyzing options trades or derivatives strategies, follow the structured
methodology in node_modules/@foundationalresearch/optionsderivatives/SKILL.md.
Use references/greeks-reference.md for detailed Greeks data and position sizing.
```

### Direct Use

You can also copy `SKILL.md` and `references/greeks-reference.md` directly into your project or paste them into any LLM conversation for immediate options analysis expertise.

## Installation

```bash
# npm
npm install @foundationalresearch/optionsderivatives

# yarn
yarn add @foundationalresearch/optionsderivatives

# pnpm
pnpm add @foundationalresearch/optionsderivatives
```

## What Gets Installed

```
@foundationalresearch/optionsderivatives/
  SKILL.md                        # Main skill file (6-step methodology)
  references/
    greeks-reference.md           # Detailed Greeks data and position sizing
  README.md                       # This file
  LICENSE                         # MIT license
```

No runtime dependencies. No executable code. Just structured knowledge for AI agents.

## Related Skills

- [@foundationalresearch/earnings](https://github.com/FoundationalResearch/earnings) -- Earnings analysis and review
- [@foundationalresearch/equityresearch](https://github.com/FoundationalResearch/equityresearch) -- Equity research and valuation
- [@foundationalresearch/macroeconomics](https://github.com/FoundationalResearch/macroeconomics) -- Macroeconomic analysis

## License

MIT -- see [LICENSE](./LICENSE) for details.
