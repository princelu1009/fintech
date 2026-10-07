---
tags: [DCPR, quiz, cross-validation]
---
# Performance evaluation

### Q1. Computing time for cross validation
For $n$ input-output pairs, building a model requires $n\alpha$ seconds, and evaluating it requires $m\beta$ seconds for $m$ pairs. We perform $k$-fold cross validation ($k$ is a factor of $n$).
1. What is the overall time required for $k$-fold cross validation?
2. What is the overall time required for leave-one-out cross validation?

> [!success]- 答案：$n(k-1)\alpha + n\beta$；$n(n-1)\alpha + n\beta$
> 每一 fold：用 $\frac{(k-1)n}{k}$ 筆訓練 → $\frac{(k-1)n}{k}\alpha$；用 $\frac nk$ 筆測試 → $\frac nk\beta$。
> 共 $k$ 個 fold：$k\left[\frac{(k-1)n}{k}\alpha + \frac nk\beta\right] = n(k-1)\alpha + n\beta$。
> LOOCV 就是 $k = n$：$n(n-1)\alpha + n\beta$。

### Q2. Computing time for cross validation
Building a model requires $2n$ seconds; evaluating requires $m$ seconds for $m$ pairs. With $1000$ pairs:
1. What is the overall time for $10$-fold cross validation?
2. What is the overall time for leave-one-out cross validation?

> [!success]- 答案：19,000 秒；1,999,000 秒
> 代 Q1 公式，$\alpha = 2$、$\beta = 1$、$n = 1000$：
> 1. $1000\times9\times2 + 1000 = 19000$
> 2. $1000\times999\times2 + 1000 = 1999000$

### Q3. Computing time for cross validation
Tuning polynomial "order" from 10 values (starting from 2) with 5-fold CV. Training (order 2) on 4 folds takes 10 s, prediction on the remaining fold takes 2 s. Overall execution time for 10 values of "order"?
1. Less than 100 seconds
2. 100 – 300 seconds
3. 300 – 600 seconds
4. More than 600 seconds

> [!success]- 答案：4（More than 600 seconds）
> order 2 時每個 fold 需 12 秒，5-fold = 60 秒；10 個 order 至少 $60\times10 = 600$ 秒。
> 而 order 越高的多項式訓練越久，所以總時間一定超過 600 秒。

### Q4. About LOOCV
Which of the following statements about LOOCV is/are correct?
1. LOOCV is time consuming and not suitable for classifiers that require lengthy training, such as neural networks.
2. LOOCV uses the dataset to the fullest to derive an objective estimate of the accuracy.
3. Stratified CV is automatically enforced in LOOCV.
4. LOOCV can be used to determine model complexity objectively.

> [!success]- 答案：1, 2, 4
> 1. ✅ 要訓練 $n$ 次模型，訓練慢的模型不適合。
> 2. ✅ 每次用 $n-1$ 筆訓練，資料利用最充分，估計偏差小。
> 3. ❌ 每次測試集只有 1 筆，不可能維持各類別比例，因此 LOOCV 無法做 stratified。
> 4. ✅ 可以用 LOOCV 的正確率比較不同複雜度（如多項式次數、k 值）來選模型。

### Q5. Stratified cross validation
Explain the meaning of "stratified m-fold cross validation".

> [!success]- 參考答案
> 把資料分成 $m$ 份時，讓**每一份中各類別的比例都和整體資料相同**，再做 $m$-fold CV。
> 這樣每個 fold 的訓練/測試集都有代表性，特別適合類別不平衡的資料，可降低正確率估計的變異。
