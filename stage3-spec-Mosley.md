# Stage 3 – Technical Specification  
**Company:** Exxon Mobil Corp (XOM)  
**Period:** FY 2025 (with FY 2024 comparison)  

---

## 1. Problem Statement

This model evaluates the financial performance and position of Exxon Mobil Corp using a structured ratio analysis framework. The objective is to assess profitability, efficiency, liquidity, and leverage using standardized financial metrics derived from Exxon’s 2025 financial statements, with 2024 as the comparison year.

The model supports decision-making by translating raw financial statement data into actionable performance indicators, enabling management and analysts to evaluate operational effectiveness, capital structure, and shareholder value creation.

---

## 2. Inputs (Known Variables)

### Balance Sheet Inputs (2025 / 2024)

- Cash & equivalents  
- Receivables  
- Inventories  
- Other current assets  
- Total current assets  
- Net PP&E  
- Total assets  
- Short-term debt  
- Accounts payable  
- Total current liabilities  
- Long-term debt  
- Total liabilities  
- Total equity  

---

### Income Statement Inputs (2025)

- `INC_revenue`  
- `INC_operating_costs`  
- `INC_depreciation`  
- `INC_sga`  
- `INC_ebit`  
- `INC_interest`  
- `INC_ebt`  
- `INC_tax`  
- `INC_net`  

---

### Cash Flow Statement Inputs (2025)

- Net income  
- Depreciation & non-cash adjustments  
- Change in working capital components  
- `CASH_cfo`  
- `CASH_capex`  
- Investing cash flows  
- Financing cash flows  

---

### Market / Analyst Inputs

- `MKT_price` = 152.51  
- `MKT_shares` = 4,179 million  
- `MKT_wacc` = assumed constant  
- `MKT_tax_rate` ≈ 27.9%  

---

## 3. Named Range Conventions

### Balance Sheet
- `BAL_cash_2025`, `BAL_cash_2024`  
- `BAL_receivables_2025`  
- `BAL_inventory_2025`  
- `BAL_total_assets_2025`, `BAL_total_assets_2024`  
- `BAL_total_liabilities_2025`  
- `BAL_equity_2025`  

### Income Statement
- `INC_revenue`  
- `INC_ebit`  
- `INC_net`  
- `INC_interest`  
- `INC_tax`  

### Cash Flow
- `CASH_cfo`  
- `CASH_capex`  

### Market Inputs
- `MKT_price`  
- `MKT_shares`  
- `MKT_wacc`  
- `MKT_tax_rate`  

### Derived Variables
- `AVG_total_assets`  
- `AVG_equity`  
- `NOPAT`  

---

## 4. Assumptions & Constraints

- Financial data sourced from annual reports (no interim adjustments)  
- Tax rate approximated using effective tax rate  
- Interest expense treated as annual and fixed  
- No off-balance-sheet liabilities included  
- Working capital simplified (aggregated changes)  
- Market values limited to equity (no market debt estimation)  
- CAPEX used as proxy for reinvestment  
- All calculations assume steady-state operations  

---

## 5. Calculation Flow

### A. Derived Inputs

```
AVG_total_assets = (BAL_total_assets_2025 + BAL_total_assets_2024) / 2
AVG_equity = (BAL_equity_2025 + BAL_equity_2024) / 2
NOPAT = INC_ebit * (1 - MKT_tax_rate)
Invested_Capital ≈ BAL_total_assets_2025 - non-interest liabilities
```

---

### B. Performance Ratios

```
MVE = MKT_price * MKT_shares
Market_to_Book = MVE / BAL_equity_2025
EVA = NOPAT - (Invested_Capital * MKT_wacc)
```

---

### C. Profitability Ratios

```
ROA = INC_net / AVG_total_assets
ROE = INC_net / AVG_equity
ROC = NOPAT / Invested_Capital

Operating_Margin = INC_ebit / INC_revenue
Net_Margin = INC_net / INC_revenue
```

---

### D. Efficiency Ratios

```
Asset_Turnover = INC_revenue / AVG_total_assets
Inventory_Turnover = COGS / AVG_inventory
Receivables_Turnover = INC_revenue / AVG_receivables

DSO = 365 / Receivables_Turnover
Days_Inventory = 365 / Inventory_Turnover
```

---

### E. Leverage Ratios

```
Debt_to_Assets = BAL_total_liabilities_2025 / BAL_total_assets_2025
Debt_to_Equity = BAL_total_liabilities_2025 / BAL_equity_2025
Interest_Coverage = INC_ebit / INC_interest
Debt_Burden = INC_net / INC_ebt
```

---

### F. Liquidity Ratios

```
Current_Ratio = BAL_current_assets / BAL_current_liabilities
Quick_Ratio = (BAL_cash + BAL_receivables_2025) / BAL_current_liabilities
Cash_Ratio = BAL_cash / BAL_current_liabilities

NWC_to_Assets = (BAL_current_assets - BAL_current_liabilities) / BAL_total_assets_2025
```

---

### G. DuPont Decomposition

```
ROA = Net_Margin × Asset_Turnover
ROE = ROA × Equity_Multiplier

Equity_Multiplier = BAL_total_assets_2025 / BAL_equity_2025
```

---

## 6. Outputs

- Ratio summary table  
- Profitability metrics (ROA, ROE, margins)  
- Liquidity metrics (current, quick, cash ratios)  
- Leverage metrics (debt ratios, coverage)  
- Market-based metrics (MVA, Market-to-Book, EVA)  
- DuPont decomposition  

---

## 7. Model Review — What Worked & What to Improve

### What Worked

- Core ratio calculations are accurate  
- Financial statements linked correctly  
- Full coverage of ratio categories  
- DuPont model implemented properly  

---

### What Needs Improvement

- Hardcoded inputs in cash flow section  
- Inconsistent naming conventions  
- Limited separation between inputs and outputs  
- No automation or scenario analysis  
- Simplified working capital treatment  
- Approximate EVA calculation  

---

### Recommended Improvements

- Standardize all named ranges  
- Separate model into Input / Calc / Output sheets  
- Add scenario modeling (base, stress, upside)  
- Expand working capital breakdown  
- Add multi-year trend analysis  
- Improve invested capital calculation for EVA  

---

## 8. Limitations & Next Steps

### Limitations

- Single-year focus limits trend analysis  
- No industry benchmarking  
- Simplified capital structure  
- No forward projections  

---

### Next Steps (Stage 4)

- Convert calculation logic into AI prompt  
- Automate ratio computation  
- Generate financial insights  
- Provide strategic recommendations  

---

## Summary

This specification transforms the Stage 2 Excel model into a structured, reproducible framework. It documents both the analytical logic and improvement opportunities, enabling automation and advanced financial analysis in Stage 4.
