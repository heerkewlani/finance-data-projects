# DCF Valuation: Unilever PLC

A discounted cash flow (DCF) model built to estimate the intrinsic value of Unilever PLC, using historical financial data (2021-2025) and forward projections.

## Methodology

- **Historical data:** Revenue, EBIT, effective tax rate, D&A, and CapEx for FY2021-FY2025, sourced from Unilever's financial statements.
- **Free Cash Flow:** Calculated as EBIT × (1 - tax rate) + D&A - CapEx for each year.
- **Growth assumption:** 4% annual FCF growth for 2026-2030, based on the lower end of Unilever's own underlying sales growth guidance (4-6%).
- **Terminal value:** Calculated using the Gordon Growth Method, with a 2.5% perpetual growth rate.
- **Discount rate:** Modeled at both 7% and 8%, reflecting typical WACC ranges for large, stable consumer goods companies (a simplified estimate was used rather than a full WACC build from beta and market risk premium data).

## Key Findings

| Discount Rate | Estimated Value Per Share | vs. Actual Market Price (£43.24) |
|---|---|---|
| 7% | ~£52.06 | Model suggests undervaluation |
| 8% | ~£40.90 | Model suggests slight overvaluation |

**The actual market price sits almost exactly between these two scenarios**, highlighting how sensitive a DCF valuation is to discount rate assumptions. A 1-percentage-point change in discount rate shifted the implied valuation by over 20%, which suggests the market is effectively pricing Unilever using a WACC somewhere between 7-8% — consistent with typical estimates for a company of its size and risk profile.

## Limitations

- Discount rate was estimated rather than calculated from a full WACC build (beta, cost of debt, capital structure weights).
- Net working capital changes were excluded from the FCF calculation for simplicity.
- Growth assumptions are based on management guidance rather than independently derived forecasts.

## Tools Used

Excel (financial modeling), data sourced from Unilever's public financial statements and stockanalysis.com.
