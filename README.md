# Replication Crisis in Finance?  
## A Unified Modeling Framework for Reconciling Pessimism and Optimism  
*Supplementary Materials Repository for Section 4 Empirical Demonstration*

---

## Contents

| File | Description |
|------|-------------|
| **Comparing The Bayesian and Frequentist Procedures for False Discovery Control: A Simulation Study** | Documentation of a simulation study showing that the Bayesian procedure in our framework is less conservative and yields more discoveries than frequentist benchmarks while maintaining comparable or lower false discovery rates   |
| **Posterior Model Probability with the Mixed Prior** | Mathematical derivations underlying the modeling framework for the empirical example |
| **USA_INVESTMENT_MONTHLY_VW_CAP** | U.S. investment-theme portfolios (capped, value-weighted monthly returns) — **Jan 1931 – Dec 2024**; sourced from <a href="https://jkpfactors.com/factor-returns" target="_blank">Global Factor Data</a>. |
| **F-F_Research_Data_5_Factors_2x3** | Five Fama–French benchmark factors (MKT, SMB, HML, RMW, CMA) — **Jul 1963 – Dec 2024**; U.S. monthly series from French’s <a href="https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html" target="_blank">data library</a>. |
| **USA_INVESTMENT_MONTHLY_VW_CAP_1963-2024** | Merge of the two datasets above, aligned **Jul 1963 – Dec 2024**; used in the empirical example. |
| **R Implementation** | R script that produces all posterior calculations and Figure 1 in the paper. |

---

## Usage

1. **Data**  
   ```r
   # R example
   data <- read.csv("USA_INVESTMENT_MONTHLY_VW_CAP_1963-2024.csv")
