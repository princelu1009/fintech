---
tags: [DCPR, quiz, optimization]
---
# Optimization

### Q1. About DSS
Which of the following statements about down-hill Simplex search (DSS) is/are correct?
1. No need to compute gradient.
2. Can only be used for continuous objective functions.
3. Can be trapped in local optimum.
4. Many variants exist.

> [!success]- 答案：1, 3, 4
> 1. ✅ DSS（Nelder-Mead）只比較函數值，透過 reflection、expansion、contraction 移動 simplex，不需梯度。
> 2. ❌ 因為只看函數值，不連續的目標函數也能用。
> 3. ✅ 仍是局部搜尋法，可能卡在 local optimum。
> 4. ✅ 有許多變形（不同的係數、重啟策略等）。

### Q2. About GAs
Which of the following statements about genetic algorithms (GAs) is/are correct?
1. GAs are slow when compared with derivative-based methods.
2. GAs can be parallelized easily.
3. The success of GAs highly depends on their encoding scheme.
4. GAs can find the global optimum.

> [!success]- 答案：1, 2, 3
> 1. ✅ 要評估大量個體、跑很多代，比用導數的方法慢。
> 2. ✅ 同一代各個體的 fitness 可以獨立平行計算。
> 3. ✅ 編碼方式決定 crossover / mutation 是否有意義，影響很大。
> 4. ❌ GA 是隨機搜尋，有機會找到全域最佳，但**不保證**。

### Q3. Lagrange multipliers
Find the maximum value of $f(x,y)=\sqrt{6-x^2-y^2}$ subject to $x+y=2$.

> [!success]- 答案：$2$
> 最大化 $f$ 等同最小化 $x^2+y^2$。在 $x+y=2$ 上，$x^2+y^2$ 在 $x=y=1$ 時最小 = 2。
> 所以 $f_{\max} = \sqrt{6-2} = 2$。
> （Lagrange：$\nabla(x^2+y^2) = \lambda\nabla(x+y) \Rightarrow 2x = 2y = \lambda$。）

### Q4. Lagrange multipliers
Find the maximum value of $f(x,y)=6-x^2-2y^2$ subject to $x+2y=3$.

> [!success]- 答案：$3$
> $\nabla f = \lambda\nabla g$：$-2x = \lambda$，$-4y = 2\lambda \Rightarrow x = y$。
> 代入 $x + 2y = 3 \Rightarrow x = y = 1$，$f = 6 - 1 - 2 = 3$。

### Q5. Lagrange multipliers for entropy function
Find the minimum and maximum values of $f(p_1, ..., p_n)=-\sum_{i=1}^n p_i \ln p_i$, where $\sum p_i=1$ and $0 \leq p_i \leq 1$.

> [!success]- 答案：最大值 $\ln n$，最小值 $0$
> - 最大：Lagrange $-\ln p_i - 1 = \lambda$，所有 $p_i$ 相等 $= 1/n$，$f = -n\cdot\frac1n\ln\frac1n = \ln n$（均勻分布最不確定）。
> - 最小：某一個 $p_i = 1$、其他為 0（約定 $0\ln0 = 0$），$f = 0$（完全確定）。

### Q6. About SA
Which of the following statements about simulated annealing (SA) is/are correct?
1. SAs are slow when compared with derivative-based methods.
2. SAs can be parallelized easily.
3. SAs do not need to compute gradient.
4. SAs can find the global optimum.

（原題題幹誤植為 GAs，選項是在問 SA。）

> [!success]- 答案：1, 3
> 1. ✅ 需要大量隨機嘗試、慢慢降溫，比梯度法慢。
> 2. ❌ SA 是一條依序前進的馬可夫鏈，每一步依賴上一步，不容易平行化（和 GA 的族群不同）。
> 3. ✅ 只需比較函數值。
> 4. ❌ 理論上降溫無限慢才保證收斂到全域最佳，實務上不保證。
