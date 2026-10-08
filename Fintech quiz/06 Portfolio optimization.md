---
tags: [fintech, quiz, portfolio-optimization]
---
# Portfolio optimization

> [!note] 核心觀念：兩資產組合
> 權重 $w_1 + w_2 = 1$，相關係數 $\rho_{12} = \dfrac{\sigma_{12}}{\sigma_1 \sigma_2}$：
> $$\mu = w_1\mu_1 + w_2\mu_2, \qquad \sigma^2 = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2w_1w_2\rho_{12}\sigma_1\sigma_2$$
> 最小變異數權重：
> $$w_1^* = \frac{\sigma_2^2 - \rho_{12}\sigma_1\sigma_2}{\sigma_1^2 + \sigma_2^2 - 2\rho_{12}\sigma_1\sigma_2}$$

> [!warning] 關於 $\rho = 1$ 的題目
> 上面的公式允許放空（權重可以 < 0 或 > 1）。$\rho = 1$ 時公式會要求放空，才能把風險壓到 0；如果不允許放空，最小風險就是全押風險較小的資產。下面兩種答案都有列，看老師的設定選。

### Q1. PO with 2 assets: No correlation
Asset 1: $\mu_1 = 0.2,\ \sigma_1 = 0.1$；Asset 2: $\mu_2 = 0.3,\ \sigma_2 = 0.2$；$\rho_{12} = 0$。
1. What are the overall $\mu$ and $\sigma$ when $w_1 = 0.4$ and $w_2 = 0.6$? (format $[\mu, \sigma]$)
2. What are $[a, b, c]$ when $\sigma^2 = a\mu^2 + b\mu + c$?
3. What are the overall $\mu$, overall $\sigma$, and $w_1$ for the minimum-variance portfolio? (format $[\mu, \sigma, w_1]$)

(Round to the fourth decimal place.)

> [!success]- 答案：[0.2600, 0.1265]；[5, −2.2, 0.25]；[0.2200, 0.0894, 0.8000]
> 1. $\mu = 0.4(0.2) + 0.6(0.3) = 0.26$；$\sigma^2 = 0.16(0.01) + 0.36(0.04) = 0.016$，$\sigma = 0.1265$。
> 2. 由 $\mu = 0.2w_1 + 0.3(1-w_1)$ 得 $w_1 = 3 - 10\mu$，$w_2 = 10\mu - 2$。
>    $\sigma^2 = 0.01(3-10\mu)^2 + 0.04(10\mu-2)^2 = 5\mu^2 - 2.2\mu + 0.25$
> 3. 拋物線頂點 $\mu = \frac{2.2}{2 \times 5} = 0.22$，$\sigma^2 = 0.008$，$\sigma = 0.0894$，$w_1 = 3 - 2.2 = 0.8$。
>    （驗算：$w_1^* = \frac{\sigma_2^2}{\sigma_1^2 + \sigma_2^2} = \frac{0.04}{0.05} = 0.8$）

### Q2. PO with 2 assets: Efficient frontier of line
In PO with 2 assets, when will the efficient frontier reduce to a straight line?

> [!success]- 答案：當 $\rho_{12} = \pm 1$（完全正相關或完全負相關）
> - $\rho = 1$：$\sigma = |w_1\sigma_1 + w_2\sigma_2|$，是連接兩資產的直線。
> - $\rho = -1$：$\sigma = |w_1\sigma_1 - w_2\sigma_2|$，是兩條直線段，在 $\sigma = 0$ 處相交（效率前緣是上面那段）。

### Q3. PO with 2 assets: Efficient frontier of line
What value of $\rho_{12}$ will reduce the efficient frontier to a straight line? (ascending vector format)

> [!success]- 答案：[-1 1]

### Q4. PO with 2 assets: Efficient frontier of parabola
In PO with 2 assets, when will the efficient frontier reduce to a parabola?

> [!success]- 答案：畫在 $(\sigma^2, \mu)$ 平面上時（任何 $\rho$ 都是）
> $\sigma^2 = a\mu^2 + b\mu + c$ 是 $\mu$ 的二次式，所以用變異數 $\sigma^2$ 當橫軸時一定是拋物線。
> 改用標準差 $\sigma$ 當橫軸時，$|\rho| < 1$ 是雙曲線，$\rho = \pm 1$ 退化成直線。
> ⚠️ 推論的答案：題目沒有給選項，如果課堂上有特別定義，以課堂為準。

### Q5. PO with 2 assets: Zero variance
When will the overall risk go to zero? What are the weights when this happens?

> [!success]- 答案：$\rho_{12} = -1$ 時，$w_1 = \dfrac{\sigma_2}{\sigma_1 + \sigma_2}$，$w_2 = \dfrac{\sigma_1}{\sigma_1 + \sigma_2}$
> $\rho = -1$ 時 $\sigma = |w_1\sigma_1 - w_2\sigma_2|$，令 $w_1\sigma_1 = w_2\sigma_2$ 即可。
> （若允許放空，$\rho = 1$ 且 $\sigma_1 \ne \sigma_2$ 時也能做到：$w_1 = \frac{\sigma_2}{\sigma_2 - \sigma_1}$，$w_2 = \frac{-\sigma_1}{\sigma_2 - \sigma_1}$。）

### Q6. PO with 2 assets: Formula for minimum variance
What are the weights for minimum-variance portfolio? Can you derive them using Lagrange multiplier?

> [!success]- 答案
> 最小化 $\sigma^2 = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2w_1w_2\sigma_{12}$，限制 $w_1 + w_2 = 1$。
> $L = \sigma^2 - \lambda(w_1 + w_2 - 1)$
> $\partial L/\partial w_1 = 2w_1\sigma_1^2 + 2w_2\sigma_{12} - \lambda = 0$
> $\partial L/\partial w_2 = 2w_2\sigma_2^2 + 2w_1\sigma_{12} - \lambda = 0$
> 兩式相減：$w_1(\sigma_1^2 - \sigma_{12}) = w_2(\sigma_2^2 - \sigma_{12})$，配合 $w_1 + w_2 = 1$：
> $$w_1 = \frac{\sigma_2^2 - \sigma_{12}}{\sigma_1^2 + \sigma_2^2 - 2\sigma_{12}}, \qquad w_2 = \frac{\sigma_1^2 - \sigma_{12}}{\sigma_1^2 + \sigma_2^2 - 2\sigma_{12}}$$

### Q7. Minimum variance with various $\rho$: overall risk
Asset 1: $\mu_1 = 0.2,\ \sigma_1 = 0.3$；Asset 2: $\mu_2 = 0.3,\ \sigma_2 = 0.4$。What is the overall risk (std) at the minimum-variance portfolio when $\rho_{12} = 1,\ 0,\ -1$? (format "d.dd")

> [!success]- 答案：ρ=1 → 0.30（不放空）/ 0.00（可放空）；ρ=0 → 0.24；ρ=−1 → 0.00
> - $\rho = 1$：不放空時全押資產 1，$\sigma = 0.30$；可放空時 $w_1 = \frac{0.4}{0.1} = 4$，$\sigma = |4(0.3) - 3(0.4)| = 0$。
> - $\rho = 0$：$w_1 = \frac{0.16}{0.25} = 0.64$，$\sigma = \frac{\sigma_1\sigma_2}{\sqrt{\sigma_1^2 + \sigma_2^2}} = \frac{0.12}{0.5} = 0.24$。
> - $\rho = -1$：$w_1 = \frac{0.4}{0.7}$，$\sigma = 0$。

### Q8. Minimum variance with various $\rho$: weight of asset 1
Asset 1: $\mu_1 = 0.2,\ \sigma_1 = 0.1$；Asset 2: $\mu_2 = 0.3,\ \sigma_2 = 0.2$。What is $w_1$ at the minimum-variance portfolio when $\rho_{12} = 1,\ 0,\ -1$? (format "d.dd")

> [!success]- 答案：ρ=1 → 1.00（不放空）/ 2.00（可放空）；ρ=0 → 0.80；ρ=−1 → 0.67
> - $\rho = 1$：公式 $w_1 = \frac{\sigma_2}{\sigma_2 - \sigma_1} = 2$（放空資產 2）；不放空則 $w_1 = 1$。
> - $\rho = 0$：$w_1 = \frac{0.04}{0.05} = 0.80$。
> - $\rho = -1$：$w_1 = \frac{\sigma_2}{\sigma_1 + \sigma_2} = \frac{0.2}{0.3} = 0.67$。

### Q9. Minimum variance with various $\rho$: overall $\mu$ and $\sigma$
Same assets as Q8. What are $[\mu, \sigma]$ at the minimum-variance portfolio when $\rho_{12} = 1,\ 0,\ -1$? (fourth decimal place)

> [!success]- 答案
> - $\rho = 1$：不放空 $[0.2000,\ 0.1000]$；可放空（$w_1 = 2$）$[0.1000,\ 0.0000]$
> - $\rho = 0$：$[0.2200,\ 0.0894]$（同 Q1）
> - $\rho = -1$：$w_1 = 2/3$，$[0.2333,\ 0.0000]$

### Q10. Computation for minimum variance
Same assets as Q8, with $\rho_{12} = 0.2$. What are the weights at the minimum-variance portfolio, and the corresponding $\mu$ and $\sigma$?

> [!success]- 答案：$w_1 = 0.8571,\ w_2 = 0.1429$，$\mu = 0.2143$，$\sigma = 0.0956$
> $\sigma_{12} = 0.2 \times 0.1 \times 0.2 = 0.004$
> $w_1 = \frac{0.04 - 0.004}{0.01 + 0.04 - 0.008} = \frac{0.036}{0.042} = \frac67 = 0.8571$
> $\mu = 0.2(0.8571) + 0.3(0.1429) = 0.2143$
> $\sigma^2 = 0.8571^2(0.01) + 0.1429^2(0.04) + 2(0.8571)(0.1429)(0.004) = 0.009143$，$\sigma = 0.0956$

### Q11. Slopes at various conditions
Asset 1: $\mu_1 = 0.2,\ \sigma_1 = 0.15$；Asset 2: $\mu_2 = 0.3,\ \sigma_2 = 0.25$。What are the slopes of the efficient frontiers when $\rho_{12} = 1$ and $-1$? (format "d.dd")

> [!success]- 答案：ρ=1 → 1.00；ρ=−1 → 0.25
> 斜率指 $\mu$–$\sigma$ 圖（橫軸 $\sigma$）上的 $\Delta\mu / \Delta\sigma$。
> - $\rho = 1$：兩資產連成直線，$\frac{0.3 - 0.2}{0.25 - 0.15} = 1.00$。
> - $\rho = -1$：效率前緣從零風險點走到資產 2，斜率 $\frac{\mu_2 - \mu_1}{\sigma_1 + \sigma_2} = \frac{0.1}{0.4} = 0.25$。
>   （零風險點：$w_1 = 0.625$，$\mu = 0.2375$，$\frac{0.3 - 0.2375}{0.25} = 0.25$ ✓）

### Q12. Objective functions in portfolio optimization
For $n$ assets, $\mu = \boldsymbol\mu^T \mathbf w$，$\sigma^2 = \mathbf w^T \Sigma \mathbf w$。What objective functions (with suitable constraints) are commonly used?
1. $\min_{\mathbf w} \mathbf w^T \Sigma \mathbf w$
2. $\max_{\mathbf w} \boldsymbol\mu^T \mathbf w$
3. $\min_{\mathbf w} \mu^2 + \sigma^2$
4. $\max_{\mathbf w} \dfrac{\mu - \mu_0}{\sigma}$
5. $\max_{\mathbf w} \mu - \beta\sigma$, where $\beta > 0$

> [!success]- 答案：1, 2, 4, 5
> 1. ✅ 最小化風險（通常加上目標報酬的限制）
> 2. ✅ 最大化報酬（通常加上風險上限的限制）
> 3. ❌ 最小化報酬沒有意義
> 4. ✅ 最大化 Sharpe ratio（$\mu_0$ 是無風險利率）
> 5. ✅ 報酬減去風險懲罰，$\beta$ 代表風險厭惡程度

### Q13. Most unlikely users of PO
下列哪一種人最不可能用到投資組合最佳化（portfolio optimization）？
1. 基金經理人
2. 自營商的操盤手
3. 70 歲的退休老人
4. 剛踏入職場的新鮮人
5. 投資上億的上市公司老闆

> [!success]- 答案：4（剛踏入職場的新鮮人）
> 資金少、通常還在累積本金，沒有太多資產需要配置。其他四種人都有大筆資金要分散風險（退休族尤其需要穩定的資產配置）。
> ⚠️ 推論的答案。
