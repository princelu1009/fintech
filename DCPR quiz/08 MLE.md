---
tags: [DCPR, quiz, MLE]
---
# MLE (Maximum Likelihood Estimation)

> [!note] 核心觀念
> MLE：找參數 $\theta$ 讓觀測資料出現的機率（likelihood）最大。通常取 log 後微分 = 0：
> $\hat\theta = \arg\max_\theta \sum_i \ln p(x_i;\theta)$

### Q1. MLE for tossing a die
Suppose you toss an imaginary 3-side die for many times and obtain $n_1$ of side 1, $n_2$ of side 2, and $n_3$ of side 3.
1. What is the most likely probabilities for sides 1, 2, and 3, respectively?
2. If you view this problem from MLE, what is your objective function (with constraint(s)) to be maximized?

> [!success]- 答案
> 1. $p_i = \dfrac{n_i}{n_1+n_2+n_3}$，$i=1,2,3$
> 2. $\max\ p_1^{n_1}p_2^{n_2}p_3^{n_3}$（或取 log：$\max\ \sum_i n_i\ln p_i$），subject to $p_1+p_2+p_3 = 1$，$p_i\ge 0$。
>
> 推導：用 Lagrange multiplier，$\frac{n_i}{p_i} = \lambda \Rightarrow p_i = n_i/\lambda$，再由總和為 1 得 $\lambda = \sum n_i$。

### Q2. MLE for 1D Gaussian PDF
Given a set of observation $\{3, 5, 7, 2, 8\}$, what are the MLE of $\mu$ and $\sigma^2$ for the 1D Gaussian PDF?

> [!success]- 答案：$\mu = 5$，$\sigma^2 = 5.2$
> $\hat\mu = \frac{3+5+7+2+8}{5} = 5$
> $\hat\sigma^2 = \frac{(-2)^2+0^2+2^2+(-3)^2+3^2}{5} = \frac{26}{5} = 5.2$
> 注意 MLE 的變異數除以 $n$（不是 $n-1$）。

### Q3. Formula for 1D Gaussian PDF
What is the formula for a 1-dim Gaussian PDF $g(x; \mu, \sigma^2)$?

> [!success]- 答案
> $g(x;\mu,\sigma^2) = \dfrac{1}{\sqrt{2\pi}\,\sigma}\exp\left[-\dfrac{(x-\mu)^2}{2\sigma^2}\right]$

### Q4. Integration of 1D Gaussian PDF
What is the value of $\int_{-\infty}^{\infty} \exp \left[ -\frac{1}{2} \left( \frac{x-\mu}{\sigma}\right)^2 \right] dx$?

> [!success]- 答案：$\sqrt{2\pi}\,\sigma$
> 因為 Gaussian PDF 積分為 1，而 PDF 前面的係數是 $\frac{1}{\sqrt{2\pi}\sigma}$，所以只剩 exp 部分的積分就是係數的倒數。

### Q5. Integration of 1D Gaussian PDF
What is the value of $\int_{-\infty}^{\infty} \exp \left[ -\frac{1}{2} \left( \frac{x-4}{2}\right)^2 \right] dx$? (Assume $\pi=3.125$, round to 1 decimal place.)

> [!success]- 答案：$5.0$
> $\sigma = 2$：$\sqrt{2\pi}\cdot 2 = 2\sqrt{6.25} = 2 \times 2.5 = 5.0$

### Q6. MLE for 1D Gaussian PDF
Given a set of observation $\{3, 5, 7, 2, 8\}$, what are the MLE of $\mu$ and $\sigma^2$ for the 1D Gaussian PDF?

> [!success]- 答案：$\mu = 5$，$\sigma^2 = 5.2$（同 Q2）

### Q7. Formula for ND Gaussian PDF
What is the formula for a n-dim Gaussian PDF $g(\boldsymbol{x}; \boldsymbol{\mu}, \Sigma)$?

> [!success]- 答案
> $g(\boldsymbol{x};\boldsymbol{\mu},\Sigma) = \dfrac{1}{(2\pi)^{n/2}|\Sigma|^{1/2}}\exp\left[-\dfrac12(\boldsymbol{x}-\boldsymbol{\mu})^T\Sigma^{-1}(\boldsymbol{x}-\boldsymbol{\mu})\right]$

### Q8. MLE for the Poisson distribution
$P(x; \lambda)=\frac{e^{-\lambda}\lambda^x}{x!}$. Given samples $\mathbf{X}=\{x_1, \cdots, x_n\}$, what is the MLE for $\lambda$?

> [!success]- 答案：$\hat\lambda = \dfrac{1}{n}\sum_{i=1}^n x_i$（樣本平均）
> $\ln L = \sum_i (-\lambda + x_i\ln\lambda - \ln x_i!)$
> $\frac{d}{d\lambda}\ln L = -n + \frac{\sum x_i}{\lambda} = 0 \Rightarrow \lambda = \frac{\sum x_i}{n}$

### Q9. MLE for the Poisson distribution (投籃機)
The goals in five one-minute plays are $\mathbf{X}=\{5, 10, 35, 20, 25\}$. What is the MLE for $\lambda$?

> [!success]- 答案：$19$
> $\frac{5+10+35+20+25}{5} = \frac{95}{5} = 19$

### Q10. MLE for the uniform distribution
$u(x;a,b) = \frac{1}{b-a}$ if $a\le x\le b$, 0 otherwise. Given $\mathbf{X}=\{x_1, \cdots, x_n\}$, what are the MLE for $a$ and $b$?

> [!success]- 答案：$\hat a = \min_i x_i$，$\hat b = \max_i x_i$
> Likelihood $= \frac{1}{(b-a)^n}$（前提是所有樣本都在 $[a,b]$ 內，否則為 0）。
> 要讓它最大就要讓 $b-a$ 最小，但區間又必須包含所有樣本，所以 $a$ 取最小值、$b$ 取最大值。

### Q11. MLE for the uniform distribution
Given $\mathbf{X}=\{3, 9, 5, 4, 1, 6, 8, 4, 6\}$, what are the MLE for $a$ and $b$? (Format: "[3 5]")

> [!success]- 答案：[1 9]
