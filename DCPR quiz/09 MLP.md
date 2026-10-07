---
tags: [DCPR, quiz, MLP, neural-network]
---
# MLP (Multilayer Perceptron)

### Q1. MLP to achieve a given decision boundary
Given the following decision boundary within the unit cube $[0, 1] \times [0, 1]$: *(原題附圖 `mlpDecBoundary.png`)*
What is the minimum configuration of an MLP to achieve the above decision boundary? (Format $m \times n \times p$, such as $3 \times 5 \times 2$.)

> [!warning] 原頁面圖片沒有一起存下來，無法確定答案。
> 解題方法：
> - 輸入層 $m$ = 輸入維度 = 2。
> - 第一個隱藏層：每個神經元對應一條直線（超平面），**數一數邊界由幾條直線組成** → $n$。
> - 單一隱藏層可組出一個凸區域（各直線 AND 起來）；若區域是多個凸區域的聯集或非凸，需要再加一層做 OR。
> - 輸出層 $p$ = 1（二元分類）。
> 例：若邊界是一個三角形，答案為 $2\times3\times1$。

### Q2. About MLPs
Which of the following statements about MLPs (multilayer perceptrons) is/are correct?
1. A three-layer MLP can approximate any complex decision boundaries.
2. Gradient vanishing could happen in either deep or wide MLPs.
3. Gradient descent is the mostly used method for training MLPs.
4. The use of the momentum term can help gradient descent avoid local minima.
5. The activation functions used in MLPs have to be continuous with finite non-differential points.

> [!success]- 答案：1, 3, 4, 5（4 有爭議）
> 1. ✅ 三層（兩個隱藏層）MLP 可組出任意形狀的決策區域：第一層畫直線、第二層 AND 成凸區域、輸出層 OR 成任意區域。
> 2. ❌ 梯度消失是因為層數「深」，連乘很多個小於 1 的導數；網路「寬」不會造成梯度消失。
> 3. ✅ 以 back-propagation 計算梯度、用 GD（及其變形 SGD、Adam）訓練。
> 4. ⚠️ 一般教科書說 momentum 可以幫助衝過淺的 local minimum，但不保證避開，所以這題可能被視為對或錯。
> 5. ✅ 要用梯度下降訓練，activation 必須連續且幾乎處處可微（例如 ReLU 只在 0 不可微）；step function 這類不連續函數無法用 GD 訓練。

### Q3. Weights in MLP for XOR problem
A 2-2-1 MLP has the following configuration: *(附圖 `mlp4xor.png`)*. The number on top of each neuron is the threshold subtracted from the net input, e.g. $x_5 = signum(x_3 w_{35}+x_4 w_{45}-1)$. Suppose the MLP has the following decision boundary for XOR (inputs/outputs 0 or 1): *(附圖 `xorDec.gif`)*
What are the values for (a) $w_{13}$, (b) $w_{23}$, and (c) $w_{14}$?

> [!warning] 原頁面圖片沒有一起存下來，無法讀出閾值與決策邊界，因此無法給確定數值。
> 解題方法：
> - XOR 需要兩條平行線把 (0,1)、(1,0) 夾在中間。
> - 隱藏神經元 3 的直線 $w_{13}x_1 + w_{23}x_2 = \theta_3$、神經元 4 的直線 $w_{14}x_1 + w_{24}x_2 = \theta_4$，對照圖中兩條線的方程式（如 $x_1+x_2=0.5$、$x_1+x_2=1.5$）即可讀出權重。
