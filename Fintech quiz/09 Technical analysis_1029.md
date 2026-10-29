---
tags: [fintech, quiz, technical-analysis]
---
# Technical analysis

### Q1. Aggregate daily candlestick charts to a weekly one
Given daily candlestick charts of 5 days (open, high, low, close):
(15, 20, 11, 17)、(18, 21, 10, 16)、(17, 19, 15, 17)、(17, 22, 11, 18)、(19, 23, 14, 19)
What is the (open, high, low, close) of the corresponding weekly candlestick chart?

> [!success]- 答案：(15, 23, 10, 19)
> - 開盤：第一天的開盤 = 15
> - 最高：五天最高價的最大值 = 23
> - 最低：五天最低價的最小值 = 10
> - 收盤：最後一天的收盤 = 19
>
> （原題寫 "daily candlestick chart"，應該是 weekly。）

### Q2. RSI computation
有一支股票過去 9 天的股價為 [3 1 4 3 4 5 3 6 13]，請根據這 9 天的資料來計算 RSI。（四捨五入至整數，不加百分比）

> [!success]- 答案：75
> 每日漲跌：−2, +3, −1, +1, +1, −2, +3, +7
> 漲幅合計 $= 3+1+1+3+7 = 15$，跌幅合計 $= 2+1+2 = 5$
> $\text{RSI} = 100 \times \dfrac{15}{15 + 5} = 75$

### Q3. Types of technical analysis
請問在技術面分析方面，最常用到的兩類方法是什麼？（以全形頓號分開）

> [!success]- 答案：型態分析、指標分析
> - 型態分析：看 K 線和價格走勢的圖形（頭肩頂、W 底、支撐壓力…）
> - 指標分析：用公式算出的技術指標（MA、RSI、KD、MACD…）
> ⚠️ 推論的答案，課堂上的用詞可能不同。
