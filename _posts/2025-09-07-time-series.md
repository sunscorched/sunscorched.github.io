---
title: 'Time Series Data'
date: 2025-09-07
permalink: /posts/2025/09/timeseries/
tags:
  - probability
  - statistics
---

### What are time series data?

A **time series** is a sequence of data points $(\vec{x}_1, y_1), (\vec{x}_2, y_2), \dots (\vec{x}_t, y_t) \dots$ where $\vec{x}_t$ represents a collection of $p$ features and $y_t$ represents a numeric variable of interest at time $t$. We often assume that our time steps are evenly spaced. Depending on the model and data set we may make additional assumptions on the $\vec{x}_t$ and $y_t$. It's possible that we don't actually have the $\vec{x}_t$ (which I will lazily just write as $x_t$ from now on). For example, we might just have $y_t$ which is a count of the number of sunspots observed on the sun at a given time $t$. We could also have, say, interest rates and inflation and we want to do predictions about inflation. So the interest rates are the features $x_t$ and inflation rates are $y_t$.


### Baseline Models

**Gaussian white noise model:** We hypothesize a data generating process of the form: $f(t) = \mu + \epsilon_t$with $\mu$ as some constant and $\epsilon_t \sim \text{NID}(0,\sigma^2)$. In this context we can call our error terms "Gaussian white noise."

The MLE fitted model will have $\hat{\mu} = \displaystyle \frac{1}{n}\sum\_{i=1}^n y_i$, and $\hat{\sigma}^2 = \displaystyle \frac{1}{n} \sum\_{i=1}^n (y - \hat{\mu})^2$.

**Average forecast:** To predict the value of $y_t$ for $t>n$ we just report $\hat{\mu} = \displaystyle \frac{1}{n}\sum_{i=1}^n y_i$.

**Note:** for this estimate to be "good", we need the assumption that the $y_t$ are independent and identically distributed.


**Gaussian Random Walk:** we model the process as $y_t = y_{t-1} + \epsilon_t$ where $\epsilon_t \sim \text{NID}(0,\sigma^2)$. We fit this model by computing $\hat{\sigma}^2 = \frac{1}{n} \displaystyle \sum_1^n (y_t - y_{t-1})^2$. 

**Naive forecast:** just set $y_t = y_n$ for $t>n$.  In other words, we just predict the last observed value!

**Linear trend:** just assume that the time series is a linear function of time plus some random noise, i.e.: $f(t) = \beta_0 + \beta_1 t + \epsilon_t$ where $\beta_0, \beta_1 \in \mathbb{R}$ and $\epsilon_t \sim \text{NID}(0,\sigma^2)$ is Gaussian white noise error term. TO fit the model, estimate $\beta_0, \ \beta_1$ with a linear regression model using the time point as the feature you are regressing on. **Linear trend forecast":** Our forecast simply predicts $y_t = \beta_0 + \beta_1 t$ for $t>n$.

**Seasonal average model:** assume that each "season" is independently following a Gaussian white noise model, where each season has a different mean but a common variance. For season $j = 0,1,2,..., T-1$ let $D_{t,j}$ be a dummy variable with $D_{t,j} = \begin{cases} 1 & \textrm{ if } t \equiv j \mod T\\ 0 & \textrm{ else} \end{cases}$ 

Then our statistical model is 
$y_t = \epsilon_t + \sum_0^{T-1} \beta_j D_{t,j}$
$\epsilon_t \sim \text{NID}(0,\sigma^2)$ 

The MLE fit model has $\hat{\beta}_j$ as the mean value for the season, in other words the average of $y_{j}, y_{j+T}, y_{j+2T}, ...$ And $\hat{\sigma}^2$ is the variance of the residuals.

**Seasonal average forecast:** simply report predicted value for a new $y_t$ with $t>n$ as the average of all observations in the same period $y_{t-T}, y_{t-2T}, y_{t-3T}, ...$

**Seasonal random walk:** we suppose each season is independently following a Gaussian random walk with the same variance. In other words we have $y_t = y_{t-T} + \epsilon_t, \epsilon_t \sim \text{NID}(0,\sigma^2)$.
We fit this model by computing $\hat{\sigma}^2 = \frac{1}{n - T} \displaystyle \sum_{T+1}^n (y_t - y_{t-T})^2$. **Seasonal naive prediction:** we predict $y_t$ to be the corresponding value from the most recently observed season.

### Stationarity

So far, our regression analysis has taken the form: $Y = f(X) + \epsilon$. This could be rewritten as $Y - f(X) = \epsilon$ and finally, using the function $F(a,b) = a - f(b)$ it could be rewritten as $F(X, Y) = \epsilon$ where $\epsilon$ is generally assumed to have a fixed distribution independent of $X$ or $Y$.  We then develop various ways to estimate $\hat{F}$ (and perhaps something about $\epsilon$) from data $(x_i, y_i)$. We could view this as attempting to find something about the relationship between $X$ and $Y$ which is **invariant**.  If we had $\epsilon  = 0$ then our relationship would be **exact**. The next best thing is to make assumptions such as, in increasing order of assumption strength, that: 
* $\epsilon$ has mean $0$ but might otherwise depend on $X$.
* $\epsilon$ has mean $0$ and constant variance, but we don't know the distribution (which may or may not depend on $X$).
* $\epsilon$ is normally distributed with mean $0$, constant variance, and is independent of $X$.

We need to believe that _something_ about the relationship between $X$ and $Y$ doesn't change in order to get started with regression modeling. We have to adjust this story a bit for time series.  Let's stick with a time series $y_t$ without any covariates. Then our best hope is that $F(t, y_{t}, y_{t-1}, y_{t-2}, \dots) = \epsilon_t$ is somehow "invariant".  For instance we might be happy if we could determine that $y_t = \sin(t) + 0.5 y_{t-1} + \epsilon_t, \epsilon_t \sim \text{NID}(0, \sigma^2)$. 

In this case the joint distribution between $y_t$ and $y_{t-1}$ is invariant under translation. We might also be happy if we could determine that $y_t = 3 + 5t + \epsilon_t, \epsilon_t - 0.5 \epsilon_{t-1} \sim \text{U}[-1,1]$. We'll discuss (weak) stationarity below but neither example is (weak) stationary.

This would also result in a joint distribution between $y_t$ and $y_{t-1}$ which is invariant under translation, but with consecutive error terms correlated in an interesting way. Our goal in time series modeling is thus to find a relation $F(t, y_{t}, y_{t-1}, y_{t-2}, \dots) = \epsilon_t $ which makes the joint distribution of the $\epsilon_t$'s "invariant" under translation.  This notion is formalized by the concept of **stationarity**. Our work is complicated by the fact that we only get to see one version of history:  we cannot "reroll the tapes".  So we generally only have access to one realization of this data generating process:  only one observation of $y_0$, $y_1$, $y_2$, ... etc.  This is one thing that makes time series modeling such a difficult task!


We say that a time series $\left\lbrace y_t  \right\rbrace$ is **strictly stationary** if the joint probability distribution of $y_{t_1}, y_{t_2}, \dots y_{t_n}$ is equal to that of $y_{t_1 + \tau}, y_{t_2 + \tau}, \dots y_{t_n + \tau}$. for any $t_1, \dots, t_n, \tau, n$. This implies that the joint distribution only depends on the intervals between $t_1, \dots, t_n$ and in particular if $n=1$: $E(y_t) =  \mu, \text{Var}(y_t) = \sigma^2$ are not functions of $t$. 

Further if $n=2$ the joint distribution of $y_{t_1}$ and $y_{t_2}$ only depends on $(t_2 - t_1)$, which is called the **lag** between $t_1$ and $t_2$. Strict stationarity is quite restrictive and we more often define a weaker sense of **stationarity.** We will say that a time series is **covariance stationary** if: $E(y_t) = \mu$ and $\text{Cov}\left( y_t, y_{t+\tau} \right) = \gamma(\tau)$. That is, the expected value is constant while the the covariance between two points is a function depending only on the elapsed time between them. This is also known as "weak sense stationary", "wide sense stationary" or just "stationary". 

Some examples of a stationary time series are: 
- White noise
- A moving average process, i.e. $y_{t} = \beta_0 \epsilon_{t} + \beta_1 \epsilon_{t-1} + \beta_2 \epsilon_{t-2} + \dots + \beta_q \epsilon_{t-q}$ with the $\epsilon \sim \text{NID}(0, \sigma^2)$.
- An autoregressive process, i.e. $y_{t} = \beta_0 y_{t-1} + \beta_1 y_{t-2} + \beta_2 y_{t-3} + \dots + \beta_q y_{t-q-1} + \epsilon_t$ with the $\epsilon \sim \text{NID}(0, \sigma^2)$.

**Note:** These last two examples are only stationary for certain values of $\beta$.

### Examples

I got this example from the following useful [link](https://www.probabilitycourse.com/chapter10/10_1_4_stationary_processes.php). The Wiki [page](https://en.wikipedia.org/wiki/Stationary_process) on stationary processes also seems useful. Consider a random process (time series) $\{y_t, t \in \mathbb{R}\}$ defined by $y_t = \cos(t+U)$ where $U \sim \text{U}(0,2\pi)$. This is a stationary in the weak sense. To see why, we first show the expected value is independent of time.

$E[y_t]=E[\cos(t+U)] = \frac{1}{2\pi}\int^{2\pi}_0 \cos(t+u)\, du = 0$ for all $t$.

The covariance we want to compute is just $E[y_t y_{t+\tau}] = E[\cos(t+U)\cos(t+\tau+U)]$ since the expected value is 0. Using sum of angle formulas, we have that:

$$
\cos(t+U)\cos(t+\tau+U) = \frac{1}{2}\cos(2t+\tau + 2U) + \frac{1}{2}\cos(t+\tau+U-(t+U))
$$

$$
=\frac{1}{2}\cos(2t+\tau + 2U)+\frac{1}{2}\cos(\tau).
$$

So the expected value above is computed as an integral. But also, the second term above does not depend on $U$ and so the integral of the 2nd term is just itself. So we have

$$
E[y_t y_{t+\tau}] = \frac{1}{2\pi}\int^{2\pi}_0 \frac{1}{2}\cos(2t + \tau+2u)\, du + \frac{1}{2}\cos(\tau) = 0+\frac{1}{2}\cos(\tau).
$$

So in this example, we have a weak sense stationary process.

If we have a weak sense stationary process, let $R_Y(\tau) = E[y_t y_{t-\tau}] = E[y_{t+\tau}y_t]$; by definition these don't depend on $t$ only the lag $\tau$. This is not the covariance but is missing a $-\mu^2$ where $\mu$ is the expected value (which is the same for all $t$ by definition of WSS). Some texts call this the **autocorrelation function** though the instructors at Erdos have a somewhat different definition given below involving the covariance and then normalizing so that the values lie in $[-1,1]$. The **autocovariance function** includes the expected values: $K_Y(t_1,t_2)= E[(y_{t_1}-\mu_{t_1})(y_{t_2}-\mu_{t_2})]$. So for a weak sense stationary process, this function would only depend on the difference $\tau = t_2-t_1$.

Note that $R_Y(0) = E[y^2_t]$. Also, $R_Y(-\tau) = R_Y(\tau)$ so this function is an **even** function.

Lastly, by Cauchy-Schwarz, $\|E[XY]\|^2 \leq E[X^2]E[Y^2]$; with equality if and only if $X=\alpha Y$. Letting $X=y_t, Y=y_{t-\tau}$, we obtain that $\|R\_Y(\tau)\|^2 = \|E[y\_t  y\_{t-\tau}]\|^2 \leq E[y^2\_t]E[y^2\_{t-\tau}] = R_Y(0)R_Y(0)$. Hence, $\|R_Y(\tau)\|\leq R_Y(0)$. Thus, $0$ is a maximum of $R_Y(\tau)$. Note that if we then add $-\mu^2$, this only vertically translates the function so the covariance will have these properties: it is even and takes its maximum at $\tau = 0$; i.e. where there is no lag. Which is what we would want: $y_{t_1}$ and $y_{t_2}$ should be more correlated when $t_1$ and $t_2$ are close and possibly not very correlated when they are far apart. Either way, the highest the correlation can be is when $t_1 = t_2$.

Also, if $X_t,Y_t$ are both WSS and their joint correlation function is only dependent on lag, then $Z_t := X_t + Y_t$ is also WSS.


### Hilbert Spaces

The main advantage of wide-sense stationarity is that it places the time-series in the context of Hilbert spaces. Let $H$ be the Hilbert space generated by $\{y_t\}$ (that is, the closure of the set of all linear combinations of these random variables in the Hilbert space of all square-integrable random variables on the given probability space). By the positive definiteness of the autocovariance function, it follows from Bochner's theorem that there exists a positive measure $\mu$ on the real line such that $H$ is isomorphic to the Hilbert subspace of $L^2(\mu)$ generated by $\{e^{2\pi i \xi t}\}$. This then gives the following Fourier-type decomposition for a continuous time stationary stochastic process: there exists a stochastic process $\omega_\xi$ with orthogonal increments such that, for all $t$, $y_t=\int e^{-2\pi i\lambda \cdot t}\,d\omega_\lambda$ where the integral on the right-hand side is interpreted in a suitable (Riemann) sense. The same result holds for a discrete-time stationary process, with the spectral measure now defined on the unit circle.

Below, we'll mention how trends and seasonality imply non-stationarity. Mathematically, one way to detect non-stationarity is to look at the Laplace transform of a time series, which will identify both exponential trends and sinusoidal seasonality (complex exponential trends). Related techniques from signal analysis such as the wavelet transform and Fourier transform may also be helpful.

### Bochner's Theorem

**Definition:** A function $f:\mathbb {R} \to \mathbb{C}$ is called **positive semi-definite** if for all real numbers $x_1,...,x_n$ the $n \times n$ matrix $A=\left(a_{ij}\right)\_{i,j=1,...,n}$ where $a_{ij}=f(x_i-x_j)$ is a positive semi-definite matrix.

**Theorem (Bochner):** A a continuous function $f$ on $\mathbb{R}$ with $f(0)=1$ is positive-definite if and only if there exists a probability measure $\mu$ on $\mathbb{R}$ such that $f(t)=\int_{\mathbb{R}} e^{-2\pi i\xi t}\,d\mu (\xi )$.

Bochner's theorem can be used to describe the serial correlation of certain type of time series. Let's work discretely as there is also a discrete version for Bochner which is essentially the same statement as above but we work on $S^1$ instead of $\mathbb{R}$.

Anyways, a sequence of random variables $\{f_{n}\}$ of mean 0 is a (wide-sense) stationary time series if the covariance $\text{Cov}(f_n,f_m)$ only depends on $n-m$ (as we've said above). The function $g(n-m)=\text{Cov}(f_n,f_m)$ is called the autocovariance function of the time series. By the mean zero assumption, $g(n-m)=\langle f_n,f_m\rangle$ where this inner product is just $L^2(\mathbb{R})$ but we can think of it as a Hilbert space of random variables with finite 2nd moments. It is then immediate that $g$ is a positive-definite function on the integers $\mathbb{Z}$ as that's how inner products behave. By Bochner's theorem, there exists a unique positive measure $\mu$ on $[0,1]$ such that the autocovariance $g(k)=\int^1_0 e^{-2\pi ikx}\,d\mu (x)$.


### Autocorrelation 
The **autocorrelation** of a time series is essentially the correlation of that time series with its future observations placed at different lags. In particular, the autocorrelation of a time series at lag $k$ is given by: 
$r_k = \text{Corr}(y_{t+k},y_t)=\frac{\text{Cov}(y_{t+k},y_{t})}{\text{StDev}(y_{t+k})\text{StDev}(y_{t})}$

If the time series is stationary, then $\text{StDev}(y_{t+k}) = \text{StDev}(y_{t})$, so their product is just the variance $\text{Var}(y_t)$. In this case we can use 
$\hat{r}_k = \frac{\displaystyle\sum_{t=1}^{n-k} \left(y_t - \overline{y}\right) \left(y_{t+k} - \overline{y} \right)}{\displaystyle\sum_{t=1}^n \left(y_t - \overline{y}\right)^2}$ 

as the sample statistic where $n$ is the last observation of the time series.


### Unit Roots and the Dickey-Fuller Test

Mathematically, how would we determine if a model exhibits stationarity?

Consider a general autoregressive model of order $p$, or AR(p), which is typically written as:
$y_t​=\phi_1​y_{t-1}​+\phi_2 ​y_{t2}​+...+ ϕ_p ​y_{t-p}​ + \epsilon_t$​.

As usual, $\epsilon_t$​ represents a white noise error term, and $\phi_j$​ are the parameters of the model. To analyze the model's stationarity properties, we form the **characteristic equation** by replacing the lag operator $L$ where $L^ky_t​=y_{t-k}​$ with a variable $z$. So for the model above, the corresponding characteristic equation is:
$1-\phi_1​z-\phi_2 ​z^2-...-\phi_p ​z^p=0$. We say the polynomial on the left is the **characteristic polynomial.**

**Definition:** A **unit root** exists when a time series model, such as an autoregressive (AR) model, has a characteristic equation with a root equal to 1. We could also study roots $r$ such that $\|r\|=1$ but these lead to other kinds of behavior such as oscillations.

For example, in a simple AR(1) process defined as $y_t​=\phi y_{t-1}​+\epsilon_t​$, the characteristic equation is $1-\phi z=0$. If $\phi=1$, the series has a unit root. For an AR(2) model $y_t​=\phi_1​ y_{t-1}​ + \phi_2​ y_{t-2}​+\epsilon_t$​, the characteristic equation becomes $1−\phi_1 ​z- \phi_2 ​z^2=0$.

The roots of this characteristic equation are critical because they determine the stationarity of the time series. Specifically, if all the roots lie outside the unit circle (i.e., $\|z\|>1$), then the process is stationary. If any root lies on or inside the unit circle, the process is non-stationary. To see why, consider the following.

* **Infinite Moving Average Representation:**
  An autoregressive process (AR) can be expressed as an infinite sum of past white noise shocks—this is known as its $MA(\infty)$ representation. When all roots of the characteristic equation are outside the unit circle, the coefficients in this infinite series decay rapidly enough. This decay guarantees that the series converges, meaning the effects of shocks diminish over time.
* **Diminishing Impact of Shocks:**
  Stationarity requires that any shock to the system has a temporary effect and that the series eventually reverts to a constant mean with a stable variance. With roots outside the unit circle, any impulse will have a fading influence, ensuring that the series doesn't “explode” over time. If $|z|<1$, then the shocks compound instead of dampen over time.
* **Mathematical Stability:**
  From a mathematical perspective, the condition on the roots ensures that the homogeneous solution to the AR equation decays to zero as time progresses. That is, we set the error to 0 and to get a homogeneous equation. The homogeneous solution will be of the form $y^h_t = A_1\lambda^t_1 +...+A_p \lambda^t_p$ where $\lambda_i = 1/r_i$ are the inverses of the roots of the characteristic polynomial. So if $|r_i|>1$ for all $i$, then $y^h_t \to 0$ as $t \to +\infty$. This decay is key for maintaining a constant variance and covariance structure (i.e., the statistical properties don't change over time).

On the flip side, if we do have a unit root:

* **Non-Stationarity:** When a time series has a unit root, its statistical properties (like mean and variance) change over time. This means the series doesn't revert to a long-term mean and its variance can grow indefinitely.
* **Permanent Shocks:** Shocks or random disturbances have a lasting impact. In a unit root process, an unexpected change affects all future values, unlike stationary series where the effect of a shock dissipates over time.
* **Forecasting Challenges:** Non-stationary series with unit roots can be harder to forecast reliably because past behavior might not adequately predict future behavior.
* **Modeling Adjustments:** Many statistical and econometric models assume stationarity. If your data have a unit root, you may need to transform it (e.g., by differencing) before applying such models to avoid issues like spurious regression. Differencing means we look at, say, $Y_t :=y_t - y_{t-1}$ and perhaps $Y_t$ will exhibit stationarity which we can try to study.


The **Dickey-Fuller test** is a statistical test used to determine whether a time series is non-stationary due to the presence of a unit root. In simpler terms:

* **Purpose:** It helps you decide if the time series data shows a consistent pattern over time (stationarity) or if it has a unit root (non-stationarity), which is a common characteristic in many economic and financial time series.
* **Null Hypothesis:** The test starts with the assumption that the series has a unit root (i.e., it is non-stationary). If you reject this hypothesis, it suggests that the series is stationary.
* **Variants:** The basic Dickey-Fuller test has been extended to the Augmented Dickey-Fuller (ADF) test, which accounts for higher-order autoregressive processes by including additional lagged terms to handle serial correlation in the data.

A common formulation of the Dickey-Fuller test starts with an autoregressive model written in differences. For example, consider the simple AR(1) model:
$y_t​=\rho y_{t-1}+\epsilon_t$​.

We can rewrite this in terms of differences by subtracting $y_{t-1}$​ from both sides:
$\Delta y_t​=y_t​ - y_{t-1}​=(\rho-1)y_{t-1}​ + \epsilon_t$​.

Letting $\gamma=\rho-1$, the equation becomes: $\Delta y_t ​= \gamma y_{t-1}​ + \epsilon_t$​.

The null hypothesis is $H_0: \gamma=0$. Under $H_0$​, the model becomes $\Delta y_t​=\epsilon_t$​, implying that $\rho=1$ and $y_t$​ has a unit root (non-stationary).

The alternative hypothesis is $H_a: \gamma<0$. This implies $\rho<1$ and the process is stationary.

The test statistic is the t-statistic for the estimated coefficient $\hat{\gamma}$: $\tau=​\hat{\gamma}/\text{SE}(\hat{\gamma})$ (divide by the standard error).

Because under the null hypothesis the process has a unit root, the distribution of $\tau$ is nonstandard—meaning it does not follow the usual t-distribution. Dickey and Fuller derived critical values from simulated distributions that must be used when deciding whether to reject $H_0$​.
