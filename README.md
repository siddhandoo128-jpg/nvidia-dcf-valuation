# NVIDIA (NVDA) DCF Valuation Model

A 10-year discounted cash flow valuation of NVIDIA Corporation built in Excel from the FY2026 Form 10-K data and Q2 FY2027 results, with scenario analysis, sensitivities, a reverse DCF and an investment memo.

**Valuation date:** 13-Oct-2026 | **Share price:** $226.32 (12-Oct-2026 close)

## Result

| Scenario | Value / share | vs. price | Probability |
|---|---|---|---|
| Bear | $72 | -68% | 25% |
| **Base** | **$207** | **-9%** | 50% |
| Bull | $321 | +42% | 25% |
| Probability-weighted | $202 | -11% | |

**Recommendation: HOLD.** The reverse DCF shows today's price requires roughly 20% revenue CAGR over FY2028-36 (base case: 14.4%).

## Repository contents

```
nvidia-dcf-valuation/
├── README.md
├── model/
│   └── NVIDIA_DCF_Valuation_Model.xlsx
└── docs/
    └── NVIDIA_Investment_Memo.pdf
```

## Workbook tabs

| Tab | Purpose |
|---|---|
| Summary | Valuation snapshot, scenario table, chart, investment view |
| Assumptions | All inputs; scenario selector in cell B3 (1 = Bear, 2 = Base, 3 = Bull) |
| Historicals | FY2024-FY2026 and H1 FY2027 income statement, cash flow items, balance sheet |
| Forecast | FY2027E-FY2036E revenue, margins, NOPAT, FCFF |
| WACC | CAPM cost of equity, cost of debt, market-value weights, beta cross-check |
| DCF | Discounting, terminal value (two methods), equity bridge, recommendation |
| Sensitivity | WACC vs. terminal growth; WACC vs. exit multiple; beta vs. ERP |
| Scenarios | Bear / Base / Bull computed in parallel, probability-weighted value |
| ReverseDCF | Revenue CAGR vs. terminal margin grid; market-implied growth |
| Checks | Integrity checks (balance sheet, cross-tab ties, sanity flags) |
| Sources | Data sources, methodology, limitations |

## Methodology

- **FCFF** = EBIT x (1 - tax) + D&A - capex - change in operating NWC. Stock-based compensation is treated as a real cost (not added back).
- **Terminal value:** value-driver perpetuity growth, TV = NOPAT x (1 - g/RONIC) / (WACC - g), cross-checked with an EV/EBITDA exit multiple; the two are blended 50/50.
- **Discounting:** mid-year convention with a stub period to the 31-Jan-2027 fiscal year-end.
- **WACC:** 11.85% (risk-free 4.7%, beta 1.60, ERP 4.5%, market-value weights).
- **Equity bridge:** adds cash, marketable securities and haircut non-marketable stakes; deducts debt. Leases are treated as operating costs.

## How to use

1. Open the workbook in Excel (or LibreOffice).
2. Change inputs on the **Assumptions** tab (blue = input, black = formula, green = cross-sheet link).
3. Flip scenarios with `Assumptions!B3`. Check the **Checks** tab reads "ALL CHECKS PASS".

## Data sources

- NVIDIA Q4/FY2026 results (8-K, Feb 2026) and Q2 FY2027 results (8-K, 26-Aug-2026), SEC EDGAR
- Share price and beta: Google Finance, TradingView; 10-year Treasury yield via FRED

## Limitations

- FY2024 figures come from filing comparatives and should be re-verified against the FY2024/FY2025 10-K.
- Risk-free rate is the latest data point found (30-Jul-2026); refresh price and rate before reuse.
- Forecast drivers, beta and ERP are analyst assumptions, not company guidance beyond Q3 FY2027.

## Disclaimer

Academic / portfolio project. Not investment advice.
