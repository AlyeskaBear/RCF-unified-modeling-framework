# Model Setup
Consider a standard OLS regression model for data $d_k$ = \{ $y_{i,k},x_{i1,k},\dots, x_{ip,k} $\} $_{i=1}^{n}$ defined by  

$$y_{i,k}=\beta_{0,k}+\beta_{1,k}x_{i1,k}+\dots+\beta_{p,k}x_{ip,k}+\varepsilon_{i,k} \qquad (1)$$ 
 
with independent random errors $\varepsilon_{i,k} \sim N(0, \sigma^{2})$ <sup id="fn1"><a href="#f1">1</a></sup>. Under this setup, let $&#x1D4DC;_ {\textrm{null},k}$ denote the null model that restricts $\beta_{0,k} \le 0$, and $&#120028;_ {\textrm{alt},k}$ denote the alternative model that restricts $\beta_{0,k} > 0$. Our goal is to compute the posterior probability of the null model, $\textrm{Pr}\(&#x1D4DC;_ {\textrm{null},k}|d_k)$, given the data $d_k$. 

We place the non-informative (Jeffreys) prior on the other coefficients $&#120631;_ {1:p,k} = (\beta_{1,k},\dots,\beta_{p,k})^\textrm{T}$ and the error variance $\sigma^{2}$

$$\pi(\beta_{1:p,k},\sigma^{2}) \propto \frac{1}{\sigma^{2}}.$$

For $\beta_{0,k}$, we use a mixed one-sided prior that encodes a belief about its sign 

$$\pi(\beta_{0,k})=\pi_\textrm{null}2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)&Iopf;(\beta_{0,k}\leq 0)+(1-\pi_\textrm{null})2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)&Iopf;(\beta_{0,k}> 0),$$

where $\phi(\cdot)$ is the standard normal distribution <sup id="fn1"><a href="#f1">2</a></sup> and $&Iopf;(\cdot)$ is an indicator function equal to one if the condition is satisfied and zero otherwise. The hyperparameter $0\leq \pi_\textrm{null} \leq 1$ is the prior probability of $&#x1D4DC;_ {\textrm{null},k}$, and $\tau>0$ is a scale parameter for $\beta_{0,k}$. This prior is essentially a $N(0, \tau^{2})$ distribution for $\beta_{0,k}$ truncated to negative or positive values, with a mixing weight $\pi_\textrm{null}$ favoring the negative side and $1-\pi_\textrm{null}$ the positive side. 

# Posterior Inference Approach

The full likelihood function for the model (1) conditioned on the data $d_k$ is

<p align="center">$$L(\beta_{0,k}, &#120631;_ {1:p,k}, \sigma^2|d_k)=(2\pi\sigma^2)^{-n&#x2215;2}\textrm{exp}[-\frac{1}{2\sigma^2}(y_{.,k}-&#119831;[\beta_{0,k}, &#120631;_ {1:p,k}])^\textrm{T}(y_{.,k}-&#119831;[\beta_{0,k}, &#120631;_ {1:p,k}])] \qquad (2)$$,</p>

where &#119831;=[&#x1D7CF;, &#119833;], with &#x1D7CF; is the column of ones (to accommodate $\beta_{0,k}$) and $&#119833;$ containing the $\mathit{p}$ covariates. Integrate the likelhood function (2) with respect to $&#120631;_ {1:p,k}$ and $\sigma^2$ under the Jeffreys prior to obtain the likelihood function for $\beta_{0,k}$  

$$L(\beta_{0,k}|d_k)=c[1+t^2(\beta_{0,k})/v]^{-\frac{v+1}{2}}$$

where 

$$t(\beta_{0,k})=\frac{\beta_{0,k}-\hat\beta_{0,k}}{\text{SE}(\hat\beta_{0,k})}, \qquad \nu=n-p-1, \qquad c=\frac{\Gamma(\frac{v+1}{2})}{\Gamma(\frac{v}{2})\sqrt{\pi v}\text{SE}(\hat\beta_{0,k})}.$$

Here, $t(\beta_{0,k})$ is the usual *t*-statistic and $\text{SE}(\hat\beta_{0,k})$ is the standard error of the OLS estimate $\hat\beta_{0,k}$. Consequently, $L(\beta_{0,k}|d_k)$ is (up to the constant *c*) the Student *t*-distribution of $\beta_{0,k}$ with $\nu$ degrees of freedom, centered at $\hat\beta_{0,k}$ and having scale $\text{SE}(\hat\beta_{0,k})$.

Then, we compute the likelihood under each sub-model, $L(&#x1D4DC;_ {\textrm{null},k}|d_k)$ and $L(&#x1D4DC;_ {\textrm{alt},k}|d_k)$, by integrating $L(\beta_{0,k}|d_k)$ over the half-normal prior on the restricted domain of $\beta_{0,k}$ for each model, respectively,

$$L(&#x1D4DC;_ {\textrm{null},k}|d_k) = \int_{-\infty}^{0} L(\beta_{0,k}|d_k)2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)d\beta_{0}$$

and

<p align="center">$$L(&#x1D4DC;_ {\textrm{alt},k}|d_k) = \int_{0}^{\infty} L(\beta_{0,k}|d_k)2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)d\beta_{0}$$.</p>

The posterior probability of $&#x1D4DC;_ {\textrm{null},k}$ is 

$$\text{Pr}(&#x1D4DC;_ {\textrm{null},k}|d_k)=\frac{\pi_\textrm{null}L(&#x1D4DC;_ {\textrm{null},k}|d_k)}{\pi_\textrm{null}L(&#x1D4DC;_ {\textrm{null},k}|d_k)+(1-\pi_\textrm{null})L(&#x1D4DC;_ {\textrm{alt},k}|d_k)}.$$

<p id="f1"><sup><sub>1</sup> <sub>The assumption of independent model errors is not essential for our framework as models with more sophisticated assumptions on data dependence fit into this framework straightforwardly. </p>  

<p id="f1"><sup><sub>2</sup> <sub>Thus, $2\tau^{-1}\phi(\beta_{0,k}&#x2215;\tau)$ is a half-normal distribution on either side of zero.</p> 
