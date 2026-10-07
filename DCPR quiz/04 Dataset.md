---
tags: [DCPR, quiz, dataset]
---
# Dataset

### Q1. Definition of imbalanced dataset
What is the definition of an imbalanced dataset?
1. A small-size dataset.
2. A small-dimensional dataset.
3. A dataset with highly non-uniform class distribution.
4. A dataset with features of very different dynamic ranges.

> [!success]- 答案：3
> 不平衡資料集指「各類別的樣本數差異很大」，例如詐騙偵測中正常交易 99%、詐騙 1%。
> 選項 4 是「特徵尺度不一」，要用正規化處理，和類別不平衡無關。

### Q2. Z normalization
Given a vector z = [1 3 5], what is its value after z-normalization?

> [!success]- 答案：$[-1.2247\ \ 0\ \ 1.2247]$（母體標準差）
> Z-normalization：$z_i' = \frac{z_i - \mu}{\sigma}$。
> $\mu = 3$，$\sigma^2 = \frac{(1-3)^2 + 0 + (5-3)^2}{3} = \frac{8}{3}$，$\sigma = 1.633$。
> 結果 $[-1.2247,\ 0,\ 1.2247]$。
> 若標準差用 $n-1$（$\sigma=2$）則為 $[-1\ 0\ 1]$。
> ⚠️ 原題檔名是 `minMaxNormalization.inc`，若考的是 min-max normalization：$\frac{z-\min}{\max-\min} = [0\ \ 0.5\ \ 1]$。

### Q3. Missing value imputation (Table 1)
Given the following dataset with missing values denoted by $X_i, i=1,2$:

| Feature name\Data index | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| Gender | ♂ | ♀ | ♂ | ♂ | ♀ | ♀ | ♀ | ♂ | ♂ |
| Age | 15 | 10 | 25 | 65 | 45 | 11 | 55 | 20 | 50 |
| Height (cm) | 160 | 130 | 158 | 179 | 164 | 148 | 168 | 154 | 132 |
| Weight (kg) | 55 | 30 | 55 | 65 | $X_1$ | 35 | 55 | 85 | 95 |
| Monthly income (k) | 2 | 1 | 30 | 120 | 80 | 2 | 100 | 30 | $X_2$ |
| BloodType | A | B | O | AB | A | B | O | AB | B |
| Class | 1 | 3 | 2 | 2 | 3 | 1 | 3 | 2 | 2 |

Find those missing values based on the following guidelines:
1. Find $X_1$ based on same-gender average
2. Find $X_1$ based on same-gender/class average
3. Find $X_1$ based on same-gender height-dependent linear interpolation
4. Find $X_2$ based on age-dependent linear interpolation
5. Find $X_2$ based on same-gender age-dependent 2-nearest-neighbor average
6. Find $X_2$ based on same-gender age-dependent linear interpolation

> [!success]- 答案：40, 42.5, 51, 90, 75, 86.25
> $X_1$ 是第 5 筆（♀、身高 164、class 3）；$X_2$ 是第 9 筆（♂、年齡 50）。
> 1. 其他女性體重 30, 35, 55 → 平均 **40**
> 2. 女性且 class 3：第 2 筆 30、第 7 筆 55 → **42.5**
> 3. 女性身高–體重：148→35、168→55，164 在兩者之間：$35 + \frac{164-148}{168-148}\times(55-35) = 35+16 =$ **51**
> 4. 全部資料年齡–收入：45→80、55→100，50 在中間 → **90**
> 5. 男性年齡：15, 25, 65, 20。離 50 最近的兩個是 65（差 15，收入 120）和 25（差 25，收入 30）→ $(120+30)/2 =$ **75**
> 6. 男性年齡–收入：25→30、65→120：$30 + \frac{50-25}{65-25}\times 90 = 30 + 56.25 =$ **86.25**

### Q4. Missing value imputation (Table 2)
Given the following dataset with missing values denoted by $X_i, i=1,2$:

| Feature name\Data index | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| Gender | ♂ | ♀ | ♂ | ♂ | ♀ | ♀ | ♀ | ♂ | ♂ |
| Age | 15 | 30 | 40 | 65 | 45 | 11 | 55 | 20 | 50 |
| Height (cm) | 165 | 130 | 158 | 175 | 164 | 148 | 168 | 185 | 172 |
| Weight (kg) | 50 | 50 | 60 | 65 | 50 | 35 | 55 | 85 | $X_1$ |
| Monthly income (k) | 2 | 80 | 60 | 120 | $X_2$ | 2 | 100 | 30 | 90 |
| BloodType | A | B | O | AB | A | B | O | AB | B |
| Class | 1 | 3 | 1 | 2 | 3 | 1 | 3 | 2 | 1 |

（小題同 Q3 的 1–6）

> [!success]- 答案：65, 55, 60.5, 75, 90, 92
> $X_1$ 是第 9 筆（♂、身高 172、class 1）；$X_2$ 是第 5 筆（♀、年齡 45）。
> 1. 其他男性體重 50, 60, 65, 85 → **65**
> 2. 男性且 class 1：第 1 筆 50、第 3 筆 60 → **55**
> 3. 男性身高排序：158→60、165→50、175→65、185→85。172 介於 165 與 175：$50 + \frac{7}{10}\times 15 =$ **60.5**
> 4. 全部資料年齡–收入：40→60、50→90，45 在中間 → **75**
> 5. 女性年齡：30→80、11→2、55→100。離 45 最近：55（差 10）、30（差 15）→ $(100+80)/2 =$ **90**
> 6. 女性 30→80、55→100：$80 + \frac{15}{25}\times 20 =$ **92**

### Q5. Missing value ratio
Given the following dataset table with missing values: *(原題附圖 `missingValueRatio.png`)*
1. What is the missing value ratio (in the input part)?
2. What is the minimum missing value ratio after deleting one row and one column from the table?

(Please put your answers into the simplest fractions.)

> [!warning] 原頁面圖片沒有一起存下來，這題無法算出數值。
> 作法：
> 1. 缺值比例 = 輸入部分（不含 output 欄）缺值格數 ÷ 輸入部分總格數。
> 2. 刪掉缺值最多的那一列和那一欄（注意兩者交叉的格子不要重複扣），再重算比例；可逐一嘗試找出最小值。

### Q6. Z normalization
Given a vector $\mathbf{x}$ = [2 3 4 5 6 7 8], what is its value after z-normalization? (Hint: $\sigma^2=\frac{\sum_{i=1}^n(x_i-\hat{\mu})^2}{n}$)

> [!success]- 答案：$[-1.5\ \ -1\ \ -0.5\ \ 0\ \ 0.5\ \ 1\ \ 1.5]$
> $\mu = 5$，$\sigma^2 = \frac{9+4+1+0+1+4+9}{7} = 4$，$\sigma = 2$。
> $\frac{x-5}{2}$ 即得答案。
