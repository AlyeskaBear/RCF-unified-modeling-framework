# Model Setup
Consider a standard linear regression model for data $d_k$ = \{ $y_{i,k},x_{i1,k},\dots, x_{ip,k} $\} $_{i=1}^{n}$ defined by  

$$y_{i,k}=\beta_{0,k}+\beta_{1,k}x_{i1,k}+\dots+\beta_{p,k}x_{ip,k}+\varepsilon_{i,k}$$
 
with independent random errors $\varepsilon_{i,k} \sim N(0, \sigma^{2})$. The assumption of independent model errors is not essential for our framework as models with more sophisticated assumptions on data dependence fit into this framework straightforwardly. Under this setup, let $&#x1D4DC;_ {\textrm{null},k}$ denote the null model that restricts $\beta_{0,k} \le 0$, and $&#120028;_ {\textrm{alt},k}$ denote the alternative model that restricts $\beta_{0,k} > 0$. Our goal is to compute the posterior probability of the null model, $\textrm{Pr}\left(&#x1D4DC;_ {\textrm{null},k}|d_k\right)$, given the data $d_k$. 

We place the non-informative (Jeffreys) priors on the slop coefficients $\beta_{1,k},\dots,\beta_{p,k}$ and the error variance $\sigma^{2}$, $\pi\left(\beta_{1:p,k},\sigma^{2}\right) \propto 1&#x2215;\sigma^{2}$. For $\beta_{0,k}$, we use a mixed one-sided prior that encodes a belief about its sign: 

$$\pi\left(\beta_{0,k}\right)=\pi_\textrm{null}2\tau^{-1}\phi\left(\beta_{0,k}&#x2215;\tau\right)&Iopf;\left(\beta_{0,k}\leq 0\right)+\left(1-\pi_\textrm{null}\right)2\tau^{-1}\phi\left(\beta_{0,k}&#x2215;\tau\right)&Iopf;\left(\beta_{0,k}> 0\right),$$

where $\phi(\cdot)$ is the standard normal distribution (thus, $2\tau^{-1}\phi\left(\beta_{0,k}&#x2215;\tau\right)$ is a half-normal distribution on either side of 0 and $&Iopf;(\cdot)$ is an indicator function equal to one if the condition is satisfied and zero otherwise. The hyperparameter $0\leq \pi_\textrm{null} \leq 1$ is the prior probability of $&#x1D4DC;_ {\textrm{null},k}$, and $\tau>0$ is a scale parameter for $\beta_{0,k}$. This prior is essentially a $N(0, \tau^{2})$ distribution for $\beta_{0,k}$ truncated to negative or positive values, with a mixing weight $\pi_\textrm{null}$ favoring the negative side and $1-\pi_\textrm{null}$ the positive side. 
