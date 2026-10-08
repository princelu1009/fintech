---
tags: [fintech, quiz, sharpe-ratio]
---
# Sharpe ratio

> [!note] 核心觀念
> $$\text{Sharpe ratio} = \frac{\bar r - r_f}{\sigma_r}$$
> 用日報酬算出來之後，年化要乘上 $\sqrt{N}$（$N$ = 一年的交易日數，常用 252）。

### Q1. Sharpe ratio computation
有一支股票過去 5 天的股價為 [5 6 7 6 8]。若無風險的年報酬率為 1%，請根據這些資料來計算（以年為主的）Sharpe ratio。（標準差用 $n-1$；答案四捨五入至小數點以下三位）

> [!success]- 答案：約 10.975（一年 252 個交易日）
> 1. 日報酬：$\frac65 - 1 = 0.2$，$\frac76 - 1 = 0.1667$，$\frac67 - 1 = -0.1429$，$\frac86 - 1 = 0.3333$
> 2. 平均 $\bar r = 0.13929$，標準差（$n-1$）$\sigma = 0.20141$
> 3. 日無風險報酬 $r_f = 0.01/252$
> 4. 年化 Sharpe $= \dfrac{0.13929 - 0.01/252}{0.20141} \times \sqrt{252} = 10.975$
>
> ⚠️ 如果課堂用一年 250 個交易日，答案是 10.931。
