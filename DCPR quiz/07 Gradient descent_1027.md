---
tags: [DCPR, quiz, gradient-descent]
---
# Gradient descent

### Q1. GD vector
Given a $3$-input function $f(x_1, x_2, x_3)=x_1^2+(x_1-x_2)^2+x_2x_3$:
1. What is the gradient of $f$ at [1 2 1]?
2. If the step size is 1, what is the next point to explore in vanilla gradient descent?

> [!success]- 答案：[0 3 2]、[1 -1 -1]
> $\frac{\partial f}{\partial x_1} = 2x_1 + 2(x_1-x_2)$，$\frac{\partial f}{\partial x_2} = -2(x_1-x_2) + x_3$，$\frac{\partial f}{\partial x_3} = x_2$
> 代入 [1 2 1]：$[2-2,\ 2+1,\ 2] = [0\ 3\ 2]$
> 下一點：$\mathbf{x} - \eta\nabla f = [1\ 2\ 1] - [0\ 3\ 2] = [1\ -1\ -1]$

### Q2. About GD
Which of the following statements about gradient descent (GD) is/are correct?
1. GD's performance is heavily dependent on the starting point and the step size.
2. GD is not likely to be trapped in local optimum.
3. GD can be used for differentiable objective functions, with some finite number of non-differentiable points.
4. GD can use the momentum term to reduce zig-zag paths.
5. GD can be used to minimize $y(x)=|x|$.

> [!success]- 答案：1, 3, 4, 5
> 1. ✅ 起點決定掉進哪個谷，步長太大會震盪、太小會很慢。
> 2. ❌ GD 只看局部斜率，很容易困在 local minimum。
> 3. ✅ 只要有限個不可微點（如 ReLU 在 0），仍可使用。
> 4. ✅ momentum 累積之前的方向，可抵消來回的 zig-zag。
> 5. ✅ $|x|$ 只有 $x=0$ 一點不可微，符合第 3 點，可用 GD（固定步長時會在 0 附近震盪，需遞減步長）。

### Q3. About derivatives
Express $y'$ in terms of $y$ for the following functions:
1. $y=\frac{1}{1+e^{-x}}$
2. $y=\frac{1-e^{-x}}{1+e^{-x}}$
3. $y=\ln(1+e^x)$
4. $y=\frac{x}{1+|x|}$

> [!success]- 答案
> 1. Sigmoid：$y' = y(1-y)$
> 2. 此函數即 $\tanh(x/2)$：$y' = \frac{1}{2}(1-y^2)$
> 3. Softplus：$e^y = 1+e^x$，$y' = \frac{e^x}{1+e^x} = \frac{e^y-1}{e^y} = 1 - e^{-y}$
> 4. Softsign：$y' = \frac{1}{(1+|x|)^2}$，又 $1-|y| = \frac{1}{1+|x|}$，所以 $y' = (1-|y|)^2$
>
> 這些式子的好處是：反向傳播時可以直接用輸出值 $y$ 算導數，不必再存 $x$。

### Q4. About derivatives (1/2)
Given $y=\ln(1+e^x)$, we can express $y'$ in terms of $y$, that is, $y'=1+g(y)$. Then what is g(0)?

> [!success]- 答案：$-1$
> 由 Q3，$y' = 1 - e^{-y}$，所以 $g(y) = -e^{-y}$，$g(0) = -1$。

### Q5. About derivatives (2/2)
Given $y=\frac{x}{1+|x|}$, we can express $y'$ in terms of $y$, that is, $y'=(1-h(y))^2$. Then what is h(-2)?

> [!success]- 答案：$2$
> $y' = (1-|y|)^2$，所以 $h(y) = |y|$，$h(-2) = 2$。

### Q6. Directional derivatives (2D)
Compute the directional derivative of $f(x, y)=x \sin(y)$ at the point $(1, \pi)$ in the direction of $(3, -4)$.

> [!success]- 答案：$\frac{4}{5} = 0.8$
> $\nabla f = (\sin y,\ x\cos y) = (0,\ -1)$。
> 方向需先單位化：$\mathbf{u} = (3,-4)/5$。
> $D_\mathbf{u} f = \nabla f\cdot\mathbf{u} = 0 + (-1)(-4/5) = 4/5$。

### Q7. Directional derivatives (3D)
Compute the directional derivative of $f(x, y, z)=x \sin(y) e^z$ at the point $(1, \pi, 0)$ in the direction of $(3, -4, 12)$. (Simplest fraction.)

> [!success]- 答案：$\frac{4}{13}$
> $\nabla f = (\sin y\, e^z,\ x\cos y\, e^z,\ x\sin y\, e^z) = (0,\ -1,\ 0)$。
> $\|(3,-4,12)\| = 13$，$D_\mathbf{u} f = (-1)(-4/13) = 4/13$。

### Q8. Gradient of a two-input function
What is the gradient of $f(x,y)=\sin(x)e^y$ at $(\pi, 0)$?

> [!success]- 答案：$[-1,\ 0]^T$
> $\nabla f = (\cos x\, e^y,\ \sin x\, e^y)$，代入 $(\pi,0)$：$(-1,\ 0)$。

### Q9. Gradient of a two-input function
If the gradient of $f(x,y)=\sin(x)e^y$ at $(\pi, 0)$ is $[a, b]^T$, what is $a+b$?

> [!success]- 答案：$-1$

### Q10. Gradient of a three-input function
What is the gradient of $f(x, y, z) = \frac{x}{y} + y\ln(z)+ze^y$?

> [!success]- 答案
> $\nabla f = \left[\ \frac{1}{y},\ \ -\frac{x}{y^2} + \ln z + z e^y,\ \ \frac{y}{z} + e^y\ \right]^T$

### Q11. Gradient of a three-input function
If the gradient of $f$ above at $(0, 1, 1)$ is $[a,b,c]^T$, then what is $a-b+c$?

> [!success]- 答案：$2$
> $a = 1$，$b = 0 + 0 + e = e$，$c = 1 + e$。
> $a - b + c = 1 - e + 1 + e = 2$。

### Q12. Gradient in matrix formulas
Give the simplest matrix format of the following expressions:
1. $\nabla \mathbf{c}^T\mathbf{x}$
2. $\nabla \mathbf{x}^T\mathbf{x}$
3. $\nabla \mathbf{c}^TA\mathbf{x}$
4. $\nabla \mathbf{x}^TA\mathbf{c}$
5. $\nabla \mathbf{x}^TA\mathbf{x}$ (where $A$ is symmetric)
6. $\nabla \mathbf{x}^TA\mathbf{x}$ (where $A$ is asymmetric)

> [!success]- 答案
> 1. $\mathbf{c}$
> 2. $2\mathbf{x}$
> 3. $A^T\mathbf{c}$（因為 $\mathbf{c}^TA\mathbf{x} = (A^T\mathbf{c})^T\mathbf{x}$）
> 4. $A\mathbf{c}$
> 5. $2A\mathbf{x}$
> 6. $(A + A^T)\mathbf{x}$
>
> 記法：把式子整理成 $\mathbf{v}^T\mathbf{x}$ 的形式，梯度就是 $\mathbf{v}$；二次式則是 $(A+A^T)\mathbf{x}$，對稱時化簡為 $2A\mathbf{x}$。

### Q13. Gradient in matrix formulas (A symmetric)
Assuming matrix A is symmetric, give the simplest expressions:
1. $\nabla \mathbf{c}^T\mathbf{x}$ 2. $\nabla \mathbf{x}^T\mathbf{x}$ 3. $\nabla \mathbf{c}^TA\mathbf{x}$ 4. $\nabla \mathbf{x}^TA\mathbf{c}$ 5. $\nabla \mathbf{x}^TA\mathbf{x}$

> [!success]- 答案：$\mathbf{c}$、$2\mathbf{x}$、$A\mathbf{c}$、$A\mathbf{c}$、$2A\mathbf{x}$
> $A$ 對稱時 $A^T = A$，所以第 3、4 題答案相同。
