---
tags: [DCPR, quiz, feature-selection]
---
# Feature selection

> [!note] 三種方法要做幾次 CV（$d$ 個特徵）
> - **One-pass ranking**：每個特徵單獨做一次 CV 排名 → $d$ 次
> - **Sequential forward selection (SFS)**：第 1 輪試 $d$ 個、第 2 輪試 $d-1$ 個…… → $d + (d-1) + \cdots + 1 = \frac{d(d+1)}{2}$ 次
> - **Exhaustive search**：所有非空子集 → $2^d - 1$ 次

### Q1. Benefit of feature selection
What are the benefits of feature selection for classification?
1. Reduce computation load
2. Increase accuracy
3. Explore correlation among features
4. Explain relationships between features and outputs

> [!success]- 答案：1, 2, 4
> 1. ✅ 特徵變少，訓練與預測都更快。
> 2. ✅ 去掉雜訊或無關特徵，常能提高準確率（也減少 overfitting）。
> 3. ❌ 特徵選取看的是「特徵對分類表現的貢獻」，不是在探索特徵彼此之間的相關性。
> 4. ✅ 被選中的特徵代表和輸出最相關，可幫助解釋模型。

### Q2. CV counts for feature selection methods ($d=12$)
Given a dataset for classification with $12$ features, how many times do we need to perform CV for: 1. One-pass ranking 2. Sequential forward selection 3. Exhaustive search

> [!success]- 答案：12、78、4095
> 1. $d = 12$
> 2. $\frac{12\times13}{2} = 78$
> 3. $2^{12}-1 = 4095$

### Q3. CV counts for feature selection methods ($d$ features)
Same as above with $d$ features.

> [!success]- 答案：$d$、$\frac{d(d+1)}{2}$、$2^d-1$

### Q4. Time for feature selection methods ($d=6$)
Given a dataset for classification with $6$ features, how many seconds do we need to perform CV for the following methods? (Assume the computing time of each CV equals the number of features involved, e.g., a 3-feature subset takes 3 seconds.)
1. One-pass ranking 2. Sequential forward selection 3. Exhaustive search

> [!success]- 答案：6 秒、56 秒、192 秒
> 1. 6 次 CV，每次 1 個特徵 → 6
> 2. 第 $k$ 輪試 $d-k+1$ 個大小為 $k$ 的子集：$1\cdot6 + 2\cdot5 + 3\cdot4 + 4\cdot3 + 5\cdot2 + 6\cdot1 = 56$
> 3. $\sum_k k\binom{6}{k} = 6\cdot 2^5 = 192$

### Q5. Time for feature selection methods ($d$ features)
Same as above with $d$ features.

> [!success]- 答案：$d$、$\frac{d(d+1)(d+2)}{6}$、$d\cdot 2^{d-1}$
> 1. $d$ 次，每次 1 秒 → $d$
> 2. $\sum_{k=1}^{d} k(d-k+1) = \frac{d(d+1)(d+2)}{6}$（代 $d=6$ 得 56 ✔）
> 3. $\sum_{k=1}^{d} k\binom{d}{k} = d\cdot 2^{d-1}$（代 $d=6$ 得 192 ✔）
