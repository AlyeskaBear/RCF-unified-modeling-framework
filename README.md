# Replication Crisis in Finance?  
## A Unified Modeling Framework for Reconciling Pessimism and Optimism  
*Supplementary Materials Repository*

---

## Contents

| File | Description |
|------|-------------|
| **Posterior Model Probability with the Mixed Prior** | Mathematical derivations underlying the modeling framework. |
| **USA_INVESTMENT_MONTHLY_VW_CAP** | U.S. investment-theme portfolios (capped, value-weighted monthly returns) — **Jan 1931 – Dec 2024**; sourced from <a href="https://jkpfactors.com/factor-returns" target="_blank">Global Factor Data</a>. |
| **F-F_Research_Data_5_Factors_2x3** | Five Fama–French factors (MKT, SMB, HML, RMW, CMA) — **Jul 1963 – Dec 2024**; from Kenneth R. French’s <a href="https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html" target="_blank">data library</a>. |
| **USA_INVESTMENT_MONTHLY_VW_CAP_1963-2024** | Merge of the two datasets above, aligned **Jul 1963 – Dec 2024**; used in the empirical example. |
| **R_Implementation** | R script that reproduces all posterior calculations and figure in the paper. |

---

## Usage

1. **Data**  
   ```r
   # R example
   data <- read.csv("USA_INVESTMENT_MONTHLY_VW_CAP_1963-2024.csv")
