---
tags: [fintech, quiz, IRR]
---
# IRR

> [!note] 核心觀念
> - 年化報酬率：總報酬 $R$ 經過 $n$ 年，年化 $= (1+R)^{1/n} - 1$。
> - IRR：讓現金流淨現值為 0 的利率。現金流 $[c_0, c_1, c_2]$ 解 $c_0 + \dfrac{c_1}{1+r} + \dfrac{c_2}{(1+r)^2} = 0$。
>   令 $x = \dfrac{1}{1+r}$，就變成一元二次方程式 $c_0 + c_1 x + c_2 x^2 = 0$。

### Q1. IRR comparison
有兩個投資案如下：
- A：十年後的總報酬是 100%
- B：六年後的總報酬是 55%

若以年複利來計算：
1. 以年化報酬率來看，何者比較好？A 或 B？
2. 若兩者年化報酬率的差距為 $n/1000$，請問 $n$ 等於多少？（請四捨五入至整數）

> [!success]- 答案：B 比較好，n = 4
> - A：$2^{1/10} - 1 = 7.177\%$
> - B：$1.55^{1/6} - 1 = 7.578\%$
>
> 差距 $0.401\% = 0.00401 \approx 4/1000$，所以 $n = 4$。

### Q2. IRR comparison
有三個投資案如下（題目寫三個，實際列了四個）：
- 5 年後的總報酬是 50%
- 10 年後的總報酬是 100%
- 15 年後的總報酬是 150%
- 20 年後的總報酬是 200%

請問哪一個投資案的績效比較好？為什麼？

> [!success]- 答案：5 年 50% 最好
> | 年數 | 總報酬 | 年化報酬率 |
> |---|---|---|
> | 5 | 50% | $1.5^{1/5}-1 = 8.45\%$ |
> | 10 | 100% | $2^{1/10}-1 = 7.18\%$ |
> | 15 | 150% | $2.5^{1/15}-1 = 6.30\%$ |
> | 20 | 200% | $3^{1/20}-1 = 5.65\%$ |
>
> 總報酬是「線性」增加的，但複利會讓同樣的報酬需要的時間越來越短，所以時間越長、年化報酬率反而越低。

### Q3. IRR computing
Given a cash flow of $[-1000,\ 3200,\ -2400]$, with yearly payment/collection and yearly compounding. What is the corresponding IRR, assuming it is less than 100%?

> [!success]- 答案：20%
> $-1000 + 3200x - 2400x^2 = 0 \Rightarrow 12x^2 - 16x + 5 = 0 \Rightarrow x = \frac{16 \pm 4}{24} = \frac{5}{6}$ 或 $\frac{1}{2}$
> $r = \frac1x - 1 = 0.2$ 或 $1$。題目說小於 100%，所以 IRR = 20%。

### Q4. IRR computing
Given a cash flow of $[100,\ -200,\ 96]$, with yearly payment/collection and yearly compounding. What is the corresponding IRR?

> [!success]- 答案：20% 或 −20%（兩個 IRR）
> $100 - 200x + 96x^2 = 0 \Rightarrow 24x^2 - 50x + 25 = 0 \Rightarrow x = \frac{50 \pm 10}{48} = \frac54$ 或 $\frac56$
> $r = \frac1x - 1 = -0.2$ 或 $0.2$。
> 現金流正負號變了兩次，所以可能有兩個 IRR。

### Q5. Cash flow from IRR
Given two potential IRRs of 0.2 and −0.5, derive the minimum (in terms of $L_1$ norm) 3-term cash flow of integers corresponding to these two IRRs.

> [!success]- 答案：$[-10,\ 17,\ -6]$（或 $[10,\ -17,\ 6]$），$L_1 = 33$
> $r = 0.2 \Rightarrow x = \frac{1}{1.2} = \frac56$；$r = -0.5 \Rightarrow x = \frac{1}{0.5} = 2$。
> 以這兩個為根的整數係數多項式：$(6x - 5)(x - 2) = 6x^2 - 17x + 10$。
> 對應 $c_0 + c_1 x + c_2 x^2$，所以現金流 $[10,\ -17,\ 6]$；整體乘 −1 也成立。
> 係數已經互質，所以這就是 $L_1$ 最小的整數解。
