---
tags: [DCPR, quiz, math]
---
# Math basics

### Q1. Distance of a point to a line
Given a point $[5, 5]$ and a line $3x+4y=50$, what is the distance between the point and the line?

> [!success]- 答案：$3$
> 點到直線距離 $= \dfrac{|ax_0+by_0-c|}{\sqrt{a^2+b^2}} = \dfrac{|15+20-50|}{5} = \dfrac{15}{5} = 3$

### Q2. Minimum absolute error
Given $\mathbf{x}=[1, 2, 3, 4, 6, 8, 18]$, compute $\arg \min_s \sum_{i=1}^n |s-x_i|$.

> [!success]- 答案：$4$（中位數）
> 最小化絕對誤差和的解是**中位數**：$s$ 往左或往右移，左右兩邊點數相等時總和最小。7 個數的中位數是第 4 個 = 4。

### Q3. Minimum square error
Given $\mathbf{x}=[1, 2, 3, 4, 6, 8, 18]$, compute $\arg \min_s \sum_{i=1}^n (s-x_i)^2$.

> [!success]- 答案：$6$（平均數）
> 對 $s$ 微分：$2\sum(s-x_i) = 0 \Rightarrow s = \bar x = \frac{42}{7} = 6$。
> 對比 Q2：平方誤差會被極端值（18）拉走，絕對誤差（中位數）較穩健。

### Q4. Quadratic form
Express $x^2+2y^2+3z^2+6xy+8yz+10xz$ in quadratic form $\mathbf{x}^TA\mathbf{x}$, where $\mathbf{x}=[x, y, z]^T$ and $A$ is symmetric.

> [!success]- 答案
> $A = \begin{bmatrix} 1 & 3 & 5 \\ 3 & 2 & 4 \\ 5 & 4 & 3 \end{bmatrix}$
> 對角線放平方項係數；交叉項係數平分到對稱的兩個位置（$6xy \to a_{12}=a_{21}=3$，$8yz \to 4$，$10xz \to 5$）。

### Q5. Quadratic form
Express the same equation in quadratic form $\mathbf{x}^TA\mathbf{x}$ ($A$ not necessarily symmetric). Then what is the sum of all elements in $A$?

> [!success]- 答案：$30$
> 不論 $A$ 是否對稱，$a_{ij}+a_{ji}$ 都等於交叉項係數，所以元素總和固定 = $1+2+3+6+8+10 = 30$。
> （也可想成 $\mathbf{1}^TA\mathbf{1} = f(1,1,1) = 30$。）

### Q6. Quadratic form
With $A$ symmetric, what is the sum of the maximum values of each column in matrix $A$?

> [!success]- 答案：$14$
> 由 Q4 的 $A$：第 1 欄最大 5、第 2 欄最大 4、第 3 欄最大 5 → $5+4+5 = 14$。
