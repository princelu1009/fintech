---
tags: [DCPR, quiz, PCA]
---
# PCA (Principal Component Analysis)

> [!note] 解題步驟
> 1. 每一列（每個維度）減去平均，得到置中資料 $\tilde X$。
> 2. 散佈矩陣 $S = \tilde X\tilde X^T$（不除以 $n$）。
> 3. $S$ 的特徵值 = 投影到對應主成分後的 **total variance**（各點到平均的距離平方和）；最大特徵值對應第一主成分。
> 4. 2×2 對稱矩陣 $\begin{bmatrix}a&b\\b&a\end{bmatrix}$ 的特徵值為 $a\pm b$，特徵向量為 $\frac{1}{\sqrt2}[1,\pm1]^T$。

### Q1. PCA computation
Given $X= \begin{bmatrix} 2 & 0 & 3 & -1 \\ 0 & -2 & -3 & 1 \end{bmatrix}$, what is the total variance after projecting the dataset onto the first principal component?

> [!success]- 答案：$16$
> 平均 $[1, -1]^T$，$S = \begin{bmatrix}10 & -6\\ -6 & 10\end{bmatrix}$，特徵值 $16, 4$。
> 第一主成分方向 $\frac{1}{\sqrt2}[1,-1]^T$，投影後 total variance = 16。

### Q2. PCA computation
Given $X= \begin{bmatrix} 3 & -1 & 2 & 0 \\ 1 & -3 & -2 & 0 \end{bmatrix}$:
1. What is the max total variance after projecting onto the first principal component?
2. What is the min total variance after projecting onto the second principal component?
3. If the second principal component is a unit vector $[a, b]^T$, what is a+b?

> [!success]- 答案：16、4、0
> 平均 $[1,-1]^T$，$S = \begin{bmatrix}10 & 6\\ 6 & 10\end{bmatrix}$，特徵值 16、4。
> 第二主成分 $\pm\frac{1}{\sqrt2}[1,-1]^T$，$a+b = 0$。

### Q3. PCA computation
Given $X= \begin{bmatrix} 6 & 0 & 4 & 2 \\ 0 & 6 & 4 & 2 \end{bmatrix}$:
1. What is the max total variance after projecting onto the first principal component?
2. If the first principal component is a unit vector $[a, b]^T$, what is a+b?

> [!success]- 答案：36、0
> 平均 $[3,3]^T$，$S = \begin{bmatrix}20 & -16\\ -16 & 20\end{bmatrix}$，特徵值 36、4。
> 第一主成分 $\pm\frac{1}{\sqrt2}[1,-1]^T$，$a+b=0$。

### Q4. PCA computation
Given $X= \begin{bmatrix} 9 & 4 & 0 & -3 & 2 & 6 \\ 6 & 6 & 4 & 0 & 0 & 2 \end{bmatrix}$, what is the total variance after projecting onto the first principal component?

> [!success]- 答案：$110$
> 平均 $[3, 3]^T$，$S = \begin{bmatrix}92 & 36\\ 36 & 38\end{bmatrix}$。
> 特徵方程 $\lambda^2 - 130\lambda + (92\cdot38 - 36^2) = \lambda^2 - 130\lambda + 2200 = 0 \Rightarrow \lambda = 110, 20$。
> 第一主成分方向 $\frac{1}{\sqrt5}[2,1]^T$。

### Q5. PCA computation
Given $X= \begin{bmatrix} 3 & -1 & 2 & 0 \\ 1 & -3 & -2 & 0 \end{bmatrix}$:
1. If the covariance matrix of $X$ is denoted by $C$, what is the sum of the first row of $3C$?
2. What is the total variance after projecting onto the first principal component?

> [!success]- 答案：16、16
> 共變異矩陣用 $n-1 = 3$：$C = S/3$，所以 $3C = S = \begin{bmatrix}10&6\\6&10\end{bmatrix}$，第一列和 = 16。
> （若 $C$ 除以 $n=4$，則 $3C$ 第一列和為 12。）
> 投影到第一主成分的 total variance = 16（同 Q2）。

### Q6. Projection onto a vector
Given $\mathbf{x}=[4, 3]^T$ and $\mathbf{y}=[7, 24]^T$, what is the (scalar) projection of $\mathbf{y}$ onto $\mathbf{x}$?

> [!success]- 答案：$20$
> $\dfrac{\mathbf{x}\cdot\mathbf{y}}{\|\mathbf{x}\|} = \dfrac{28 + 72}{5} = 20$

### Q7. PCA properties
Which of the following statements about PCA is/are correct?
1. PCA is an unsupervised algorithm for dimensionality reduction.
2. PCA can be used to find the best fitting hyperplane with total least-squares.
3. Both PCA and k-means clustering serve the purpose of dimensionality reduction.
4. Zero justification is necessary before computing covariance for PCA.
5. A symmetric matrix have orthogonal eigenvectors corresponding to different eigenvalues.

> [!success]- 答案：1, 2, 4, 5
> 1. ✅ 不用標籤，找變異最大的方向來降維。
> 2. ✅ 最小的主成分方向就是 total least-squares 最佳超平面的法向量（最小化點到平面的垂直距離平方和）。
> 3. ❌ k-means 是減少資料「筆數」（data reduction），不是降維。
> 4. ✅ 必須先減去平均（zero-mean / zero justification）再算共變異矩陣。
> 5. ✅ 對稱矩陣不同特徵值對應的特徵向量必定正交，所以主成分彼此正交。
