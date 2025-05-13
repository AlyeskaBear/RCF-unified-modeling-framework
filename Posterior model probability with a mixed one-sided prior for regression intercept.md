# Model Setup
Consider a standard linear regression model for data $d_k$ = \{ $y_{i,k},x_{i1,k},\dots, x_{ip,k}$ \} $_{i=1}^{n}$ defined by  

$$y_{i,k}=\beta_{0,k}+\beta_{1,k}x_{i1,k}+\dots+\beta_{p,k}x_{ip,k}+\varepsilon_{i,k}$$
 
with independent random errors $\varepsilon_{i,k} \sim N(0, \sigma^{2})$. The assumption of independent model errors is not essential for our framework as models with more sophisticated assumptions on data dependence fit into this framework straightforwardly. 

We place the non-informative (Jeffreys) priors on the slop coefficients $\beta_{1,k},\dots,\beta_{p,k}$ and the error variance $\sigma^{2}$, $\pi(\beta_{1:p,k},\sigma^{2}) \propto 1/\sigma^{2}$. For the intercept $\beta_{0,k}$ we use a mixed one-sided prior that encodes a belief about its sign:
