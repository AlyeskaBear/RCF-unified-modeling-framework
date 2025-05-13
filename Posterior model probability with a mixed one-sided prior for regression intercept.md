# Model Setup
Consider a standard linear regression model for data $d_k$ = \{ $y_{i,k},x_{i1,k},\dots, x_{ip,k} $\} $_{i=1}^{n}$ defined by  

$$y_{i,k}=\beta_{0,k}+\beta_{1,k}x_{i1,k}+\dots+\beta_{p,k}x_{ip,k}+\varepsilon_{i,k} \qquad (1)$$ 
 
with independent random errors $\varepsilon_{i,k} \sim N(0, \sigma^{2})$. The assumption of independent model errors is not essential for our framework as models with more sophisticated assumptions on data dependence fit into this framework straightforwardly. Under this setup, let $&#x1D4DC;_ {\textrm{null},k}$ denote the null model that restricts $\beta_{0,k} \le 0$, and $&#120028;_ {\textrm{alt},k}$ denote the alternative model that restricts $\beta_{0,k} > 0$. Our goal is to compute the posterior probability of the null model, $\textrm{Pr}\left(&#x1D4DC;_ {\textrm{null},k}|d_k\right)$, given the data $d_k$. 

We place the non-informative (Jeffreys) prior on the slop coefficients $\beta_{1,k},\dots,\beta_{p,k}$ and the error variance $\sigma^{2}$

$$\pi(\beta_{1:p,k},\sigma^{2}) \propto \frac{1}{\sigma^{2}}.$$

For $\beta_{0,k}$, we use a mixed one-sided prior that encodes a belief about its sign: 

$$\pi\left(\beta_{0,k}\right)=\pi_\textrm{null}2\tau^{-1}\phi\left(\beta_{0,k}&#x2215;\tau\right)&Iopf;\left(\beta_{0,k}\leq 0\right)+\left(1-\pi_\textrm{null}\right)2\tau^{-1}\phi\left(\beta_{0,k}&#x2215;\tau\right)&Iopf;\left(\beta_{0,k}> 0\right),$$

where $\phi(\cdot)$ is the standard normal distribution (thus, $2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)$ is a half-normal distribution on either side of 0 and $&Iopf;(\cdot)$ is an indicator function equal to one if the condition is satisfied and zero otherwise. The hyperparameter $0\leq \pi_\textrm{null} \leq 1$ is the prior probability of $&#x1D4DC;_ {\textrm{null},k}$, and $\tau>0$ is a scale parameter for $\beta_{0,k}$. This prior is essentially a $N(0, \tau^{2})$ distribution for $\beta_{0,k}$ truncated to negative or positive values, with a mixing weight $\pi_\textrm{null}$ favoring the negative side and $1-\pi_\textrm{null}$ the positive side. 

# Posterior Inference Approach

W

With a flat prior on the other regression coefficients \beta_{1,k},\dots,\beta_{p,k} and on $\sigma^{2}$, the posterior inference for $\beta_{0,k}$ follows standard results. In particular, if assigning $\beta_{0,k}$ the continuous, unrestricted $N(0, \tau^{2})$ prior, the marginal posterior for $\beta_{0,k}$ (after integrating out the other coefficients and $\sigma^{2}$) is a Student-*t* distribution centered at the ordinary least squares (OLS) estimate. Specifically, if $\hat\beta_{0,k}$ is the OLS estimate of $\beta_{0,k}$ and $\text{SE}(\hat\beta_{0,k})$ its standard error, Student-*t* distribution has
- Degrees of freedom: $\nu = n - (p+1)$ (residual degrees of freedom).
- Location: $\hat\beta_{0}$ (OLS estimate).
- Scale: $s \cdot \text{SE}(\hat\beta_{0})$, where $s^2$ is the OLS residual variance estimate.

To incorporate the one-sided prior, we use a mixture updating approach: Essentially, we treat the two halves of the prior (negative vs. positive $\beta_{0,k}$) as two competing models. We compute the marginal likelihood of the data under each sub-model by integrating the likelihood times the truncated prior over the allowed domain of $\beta_{0,k}$. Let $L(\beta_{0}) = p(d_k \mid \beta_{0}, M_{\text{rest}})$ be the likelihood (with other parameters integrated out or evaluated at their posterior modes for simplicity). Then:
Null model evidence ($M_{0,k}$): $E_0 = \int_{-\infty}^{0} L(\beta_{0}) \cdot \frac{2}{\tau}\varphi(\beta_{0}/\tau),d\beta_{0}$ (times $\pi_0$ if treating $\pi_0$ as prior model probability).
Alternative model evidence ($M_{1,k}$): $E_1 = \int_{0}^{\infty} L(\beta_{0}) \cdot \frac{2}{\tau}\varphi(\beta_{0}/\tau),d\beta_{0}$ (times $(1-\pi_0)$).
Given the prior odds $\pi_0:(1-\pi_0)$, the posterior probability of the null is:
