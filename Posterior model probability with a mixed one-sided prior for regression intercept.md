# Model Setup
Consider a standard linear regression model for data $d_k$ = \{ $y_{i,k},x_{i1,k},\dots, x_{ip,k}$ \} $_{i=1}^{n}$defined by  

$$y_{i,k}=\beta_{0,k}+\beta_{1,k}x_{i1,k}+\dots+\beta_{p,k}x_{ip,k}+\varepsilon_{i,k}$$
 
with independent random errors $\varepsilon_{i,k} \sim N(0, \sigma^{2})$. The assumption of independent model errors is not essential for our framework as models with more sophisticated assumptions on data dependence fit into this framework straightforwardly. Under this setup, let $&#x1D4DC;_ {\textrm{null},k}$ denote the null model that restricts $\beta_{0,k} \le 0$, and $&#120028;_ {\textrm{alt},k}$ denote the alternative model that restricts $\beta_{0,k} > 0$ 

We place the non-informative (Jeffreys) priors on the slop coefficients $\beta_{1,k},\dots,\beta_{p,k}$ and the error variance $\sigma^{2}$, $\pi(\beta_{1:p,k},\sigma^{2}) \propto 1&#x2215;\sigma^{2}$. For the intercept $\beta_{0,k}$ we use a mixed one-sided prior that encodes a belief about its sign: 

$$\pi(\beta_{0,k})=\pi_\textrm{null}2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)&Iopf;(\beta_{0,k}\leq 0)+(1-\pi_\textrm{null})2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)&Iopf;(\beta_{0,k}> 0),$$

where $\phi(\cdot)$ is the standard normal distribution, so $2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)$ is a half-normal distribution on either side of 0. The hyperparameter $0\leq \pi_0 \leq 1$ is the prior probability of $&#x1D4DC;_ {\textrm{null},k}$, and $\tau>0$ is a scale parameter (spread) for $\beta_{0,k}$.   
