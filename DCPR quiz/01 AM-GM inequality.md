---
tags: [DCPR, quiz, AM-GM]
---
# AM-GM inequality

> [!note] 核心觀念
> 算幾不等式：$\frac{a_1+\cdots+a_n}{n} \ge \sqrt[n]{a_1\cdots a_n}$，等號成立於 $a_1=\cdots=a_n$。
> 解「表面積固定、體積最大」類題目的技巧：把表面積拆成幾項，使它們的**乘積**剛好是體積的某個次方，再用算幾不等式。

### Q1. Max volume of an open box
What is the maximum volume for a rectangular box (no top) made from 12 square meters of cardboard?

> [!success]- 答案：$4\ \text{m}^3$
> 長寬高 $x, y, z$，表面積 $xy + 2xz + 2yz = 12$，體積 $V=xyz$。
> 三項乘積 $(xy)(2xz)(2yz) = 4(xyz)^2 = 4V^2$。
> 由算幾：$4V^2 \le \left(\frac{12}{3}\right)^3 = 64 \Rightarrow V \le 4$。
> 等號：$xy=2xz=2yz=4 \Rightarrow x=y=2,\ z=1$。

### Q2. Max volume of an open box (square base)
What is the maximum volume for a rectangular box (square base, no top) made from 12 square meters of cardboard?

> [!success]- 答案：$4\ \text{m}^3$
> 底邊 $x$、高 $h$：$x^2 + 4xh = 12$，拆成 $x^2 + 2xh + 2xh$。
> 乘積 $x^2 \cdot 2xh \cdot 2xh = 4x^4h^2 = 4V^2 \le 64 \Rightarrow V\le 4$。
> 等號：$x^2 = 2xh = 4 \Rightarrow x=2,\ h=1$（和 Q1 結果相同，因為 Q1 的最佳解本來就是正方形底）。

### Q3. Max volume of an open cylinder
What is the maximum volume for a cylinder (no top) made from 12 square meters of cardboard?

> [!success]- 答案：$V = \dfrac{8}{\sqrt{\pi}} \approx 4.51\ \text{m}^3$
> 表面積 $\pi r^2 + 2\pi r h = \pi r^2 + \pi r h + \pi r h = 12$，體積 $V=\pi r^2 h$。
> 乘積 $\pi r^2 \cdot \pi r h \cdot \pi r h = \pi^3 r^4 h^2 = \pi V^2 \le 4^3 = 64$
> $\Rightarrow V \le \frac{8}{\sqrt\pi}$。等號：$\pi r^2 = \pi r h = 4 \Rightarrow r = h = \frac{2}{\sqrt\pi}$。

### Q4. An open box with max volume
A rectangular box without a top (a topless box) is to be made from 12 square foot of cardboard. Let x, y, and z be the length (in foot) of each side of the box. What is $x+y+z$ when the volume of the box is maximized?

> [!success]- 答案：$5$
> 同 Q1，最大體積時 $x=y=2,\ z=1$，所以 $x+y+z=5$。

### Q5. How to create an open box with max volume
Given a square cardboard, we want to cut a square of each of the four corners such that the remaining cardboard can be folded into a topless box with a square base. What is the ratio of its base side to its height when the volume is maximized?

> [!success]- 答案：底邊 : 高 $= 4 : 1$
> 紙板邊長 $a$，四角各剪邊長 $h$ 的正方形，底邊 $b = a-2h$，$V = (a-2h)^2 h$。
> 寫成 $V = \frac14 (a-2h)(a-2h)(4h)$，三項和 $=2a$ 為常數，由算幾在 $a-2h = 4h$ 時最大。
> 所以 $h = a/6$、$b = 2a/3 = 4h$，比例為 4。
