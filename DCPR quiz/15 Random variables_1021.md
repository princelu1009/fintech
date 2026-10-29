---
tags: [DCPR, quiz, probability]
---
# Random variables

### Q1. Mean/variance of tossing a dice
Given a fair dice with face value X: 1. $E(X)$=? 2. $V(X)$=? (Simplest fractions.)

> [!success]- 答案：$E(X) = 7/2$，$V(X) = 35/12$
> $E(X) = \frac{1+\cdots+6}{6} = \frac72$
> $E(X^2) = \frac{1+4+9+16+25+36}{6} = \frac{91}{6}$
> $V(X) = \frac{91}{6} - \frac{49}{4} = \frac{182-147}{12} = \frac{35}{12}$

### Q2. Mean/variance of a linear combination of discrete variables
Two fair dice $X$, $Y$. What are $E(Z)$ and $V(Z)$ if $Z=X+2Y$?

> [!success]- 答案：$E(Z) = 21/2$，$V(Z) = 175/12$
> $E(Z) = E(X) + 2E(Y) = \frac72 + 7 = \frac{21}{2}$
> $X, Y$ 獨立：$V(Z) = V(X) + 4V(Y) = 5\times\frac{35}{12} = \frac{175}{12}$
> 注意變異數的係數要平方。

### Q3. Covariance matrix of two random variables
$X$ = [1, 3, 2, 1, 3], $Y$ = [2, 4, 5, 4, 5]. Compute the covariance matrix (divide by $n-1$, round to 2 decimals).

> [!success]- 答案
> $\begin{bmatrix} 1.00 & 0.75 \\ 0.75 & 1.50 \end{bmatrix}$
> $\bar X = 2$，$\bar Y = 4$。
> 偏差：$X$：[-1, 1, 0, -1, 1]，$Y$：[-2, 0, 1, 0, 1]
> $V(X) = 4/4 = 1$，$V(Y) = (4+0+1+0+1)/4 = 1.5$，$\text{Cov} = (2+0+0+0+1)/4 = 0.75$

### Q4. Mean, median, and mode of a PDF
Given the PDF-like histogram plot *(原題附圖 `meanMedianMode4pdf01.png`)*, compute its mode, median, and mean. (Assume $\sqrt3 = 1.732$.)

> [!warning] 原頁面圖片沒有一起存下來，無法算出數值。作法：
> - Mode：PDF 最高點的 $x$。
> - Median：找 $m$ 使 $\int_{-\infty}^{m} p(x)dx = 0.5$（題目提示 $\sqrt3$，代表解中位數時會出現開根號）。
> - Mean：$\int x\,p(x)dx$；分段的直方圖可用各段面積 × 該段中心加總。

### Q5. Mean, median, and mode of a PDF
Given the PDF-like histogram plot *(原題附圖 `meanMedianMode4pdf02.png`)*, compute its mode, median, and mean.

> [!warning] 原頁面圖片沒有一起存下來，無法算出數值，作法同 Q4。

### Q6. About Poisson distribution
$p(x; \lambda)=\frac{e^{-\lambda}\lambda^x}{x!}$. Prove that $\sum_{x=0}^\infty p(x; \lambda)=1$.

> [!success]- 證明
> $\sum_{x=0}^\infty \frac{e^{-\lambda}\lambda^x}{x!} = e^{-\lambda}\sum_{x=0}^\infty\frac{\lambda^x}{x!} = e^{-\lambda}\cdot e^{\lambda} = 1$
> 利用 $e^\lambda$ 的泰勒展開 $e^\lambda = \sum_{x=0}^\infty \frac{\lambda^x}{x!}$。
