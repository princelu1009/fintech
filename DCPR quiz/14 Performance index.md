---
tags: [DCPR, quiz, performance-index, ROC]
---
# Performance index

> [!note] 名詞
> - WER（word error rate）：以詞為單位的編輯距離 ÷ 正解詞數
> - CER（character error rate）：以字元為單位（英文字母也逐字計算）
> - MER（mixed error rate）：中文以「字」、英文以「詞」為單位
> - 以下閾值規則：likelihood $\ge\theta$ 判為 positive

### Q1. Performance indices of ASR
- Groundtruth: 豆腐 是 我 最 喜歡 的 食物
- Prediction: Tofu 是 我 最 喜歡 的 師父

Compute WER, CER, MER (simplest fractions).

> [!success]- 答案：WER = 2/7、CER = 3/5、MER = 2/5
> - WER：7 個詞，「豆腐→Tofu」「食物→師父」2 個替換 → $2/7$
> - CER：正解 10 個字；預測為 T,o,f,u,是,我,最,喜,歡,的,師,父。「豆腐」→「Tofu」= 2 替換 + 2 插入 = 4，「食物→師父」= 2 → $6/10 = 3/5$
> - MER：預測單位為 Tofu,是,我,最,喜,歡,的,師,父。「豆腐→Tofu」= 1 替換 + 1 刪除 = 2，加上 2 → $4/10 = 2/5$

### Q2. Performance indices of ASR
- Groundtruth: Typhoon 不 要 來 台灣
- Prediction: 颱風 不 要 來 臺灣

> [!success]- 答案：WER = 2/5、CER = 2/3、MER = 1/2
> - WER：5 個詞，Typhoon→颱風、台灣→臺灣 2 個替換 → $2/5$
> - CER：正解 T,y,p,h,o,o,n,不,要,來,台,灣 = 12；Typhoon（7）→颱風（2）= 2 替換 + 5 刪除 = 7，台→臺 = 1 → $8/12 = 2/3$
> - MER：正解單位 Typhoon,不,要,來,台,灣 = 6；Typhoon→颱,風 = 1 替換 + 1 插入 = 2，台→臺 = 1 → $3/6 = 1/2$

### Q3. Cost-sensitive classification

| Groundtruth | 0 | 1 | 0 | 1 | 0 | 0 | 1 |
|---|---|---|---|---|---|---|---|
| Likelihood | 3 | 4 | 5 | 6 | 7 | 8 | 9 |

1. With cost $f(\alpha)$ = FPC + $\alpha$·FNC, plot the cost function w.r.t. $\theta$ when $\alpha$ is 1 and 3.
2. Best $\theta$ and cost when $\alpha=1$?
3. Best $\theta$ and cost when $\alpha=3$?

> [!success]- 答案
>
> | $\theta$ 範圍 | FPC | FNC | cost (α=1) | cost (α=3) |
> |---|---|---|---|---|
> | $\theta\le3$ | 4 | 0 | 4 | 4 |
> | $3<\theta\le4$ | 3 | 0 | **3** | **3** |
> | $4<\theta\le5$ | 3 | 1 | 4 | 6 |
> | $5<\theta\le6$ | 2 | 1 | 3 | 5 |
> | $6<\theta\le7$ | 2 | 2 | 4 | 8 |
> | $7<\theta\le8$ | 1 | 2 | 3 | 7 |
> | $8<\theta\le9$ | 0 | 2 | **2** | 6 |
> | $\theta>9$ | 0 | 3 | 3 | 9 |
>
> 1. 畫圖：橫軸 $\theta$，縱軸 cost，是上表的階梯函數。
> 2. $\alpha=1$：最佳 $\theta \in (8, 9]$，cost = **2**。
> 3. $\alpha=3$：最佳 $\theta \in (3, 4]$，cost = **3**。漏判（FN）代價變高，所以閾值往下調，寧可多判 positive。

### Q4. End points of ROC, DET, PRC
With $N$ negative and $P$ positive samples, what are the coordinates of the two end points (ordered by X) of:
- ROC (y=TPR vs. x=FPR)
- DET (y=FNR vs. x=FPR)
- PRC (y=precision vs. x=recall), where the sample with the biggest likelihood is positive.
- PRC, where the sample with the biggest likelihood is negative.

(If an end point has 0/0, adopt the next/previous non-NaN point.)

> [!success]- 答案
> - ROC：$(0,0)$、$(1,1)$
> - DET：$(0,1)$、$(1,0)$
> - PRC（最高分是正例）：$\left(\frac1P,\ 1\right)$、$\left(1,\ \frac{P}{P+N}\right)$
> - PRC（最高分是負例）：$(0,\ 0)$、$\left(1,\ \frac{P}{P+N}\right)$
>
> 說明：閾值高於所有樣本時沒有預測 positive，precision = 0/0 不能畫，所以改取「只有最高分一筆被判 positive」的點：若它是正例，recall = 1/P、precision = 1；若是負例，recall = 0、precision = 0。閾值最低時全部判 positive，recall = 1、precision = P/(P+N)。

### Q5. Properties of ROC, DET, PRC
Types: Increasing ($x<y \Rightarrow f(x)\le f(y)$), Decreasing, Monotonically increasing ($<$), Monotonically decreasing, None. Give the type of:
1. FPR vs. $\theta$ 2. FNR vs. $\theta$ 3. Precision vs. $\theta$ 4. Recall vs. $\theta$ 5. DET (FNR vs. FPR) 6. ROC (TPR vs. FPR) 7. PRC (precision vs. recall)

> [!success]- 答案
> 1. FPR vs. θ：Decreasing（θ 變大，判 positive 的變少，FPR 不增，但可能持平）
> 2. FNR vs. θ：Increasing
> 3. Precision vs. θ：None（會上下跳動）
> 4. Recall vs. θ：Decreasing
> 5. DET：Decreasing
> 6. ROC：Increasing
> 7. PRC：None
>
> 都只是「不嚴格」的遞增/遞減，因為閾值落在兩個樣本之間時數值不變，曲線會有水平或垂直段。

### Q6. Properties of ROC, DET, PRC
In a ROC plot, usually the waveform is stairwise. If you see a ROC curve with a slope, what can you conclude? *(原題附圖 `detRocPlotWithSlope01.png`)*

> [!success]- 答案
> 有**正例與負例的 likelihood 相同（ties）**。閾值跨過這個分數時，TP 和 FP 同時增加，所以曲線出現斜線而不是一格一格的階梯。

### Q7. PIs from confusion matrices
Compute the following from the given confusion matrix *(原題附圖 `confusionMatrix.png`)*: Accuracy, TPR, TNR, FPR, FNR, Precision, F-measure (simplest fractions).

> [!warning] 原頁面圖片沒有一起存下來，無法算出數值。公式如下：
> - Accuracy $= \frac{TP+TN}{TP+TN+FP+FN}$
> - TPR（recall）$= \frac{TP}{TP+FN}$
> - TNR（specificity）$= \frac{TN}{TN+FP}$
> - FPR $= \frac{FP}{FP+TN} = 1 - \text{TNR}$
> - FNR $= \frac{FN}{FN+TP} = 1 - \text{TPR}$
> - Precision $= \frac{TP}{TP+FP}$
> - F-measure $= \frac{2PR}{P+R} = \frac{2TP}{2TP+FP+FN}$
>
> 註：題目把 FPR 寫成「miss rate」，但 miss rate 通常指 FNR，FPR 應為 false alarm rate。

### Q8. Performance indices for imbalanced datasets
Which are more suitable for evaluating a classifier for imbalanced datasets?
1. RMSE 2. auROC 3. auPRC 4. Accuracy 5. F-measure 6. Coefficient of $R^2$

> [!success]- 答案：3, 5（2 次之）
> - auPRC、F-measure 都聚焦在少數類別（positive）的 precision 與 recall，最適合不平衡資料。
> - auROC 也常用，但負例很多時 FPR 變化很小，會顯得過度樂觀，所以不如 auPRC。
> - Accuracy 會被多數類別主導（全猜負例也有 99%）；RMSE、$R^2$ 是回歸指標。

### Q9. Lift chart: Compute cumulated recall from binwise precision
Given the partial lift chart with binwise precision only *(原題附圖 `liftChart03question.png`)*, compute the heights of the first 2 bins of its cumulated recall curve. (Format [a b], two decimals.)

> [!warning] 原頁面圖片沒有一起存下來，無法算出數值。作法：
> 每個 bin 的正例數 = bin precision × bin 樣本數。
> cumulated recall（第 $k$ 個 bin）= 前 $k$ 個 bin 的正例數總和 ÷ 全部正例數 $P$。

### Q10. Lift chart of a perfect binary classifier
Plot the lift chart of a perfect binary classifier when P=335 and N=665, with 10 bins.

> [!success]- 答案
> 共 1000 筆，每個 bin 100 筆；完美分類器把 335 個正例全部排在最前面。
>
> | bin | 1 | 2 | 3 | 4 | 5–10 |
> |---|---|---|---|---|---|
> | bin precision | 1 | 1 | 1 | 0.35 | 0 |
> | cumulated recall | 0.2985 | 0.5970 | 0.8955 | 1 | 1 |
>
> （100/335 = 0.2985，200/335 = 0.5970，300/335 = 0.8955）

### Q11. Lift chart of a random-guess binary classifier
Plot the ideal lift chart of a random-guess binary classifier, with 10 bins and 3N=7P.

> [!success]- 答案
> $3N = 7P \Rightarrow P:N = 3:7$，正例佔 30%。隨機猜測時每個 bin 的正例比例都和整體一樣。
> - bin precision：每個 bin 都是 **0.3**
> - cumulated recall：0.1, 0.2, 0.3, …, 1.0（一條對角直線）

### Q12. Mean average precision
Result 1: y n y；Result 2: n n y. If mAP@3 = p/q (simplest), what is p+q?

> [!success]- 答案：$19$
> AP = 每個命中位置的 precision 的平均。
> - Result 1：命中在第 1、3 位 → $(1/1 + 2/3)/2 = 5/6$
> - Result 2：命中在第 3 位 → $1/3$
> - mAP $= (5/6 + 1/3)/2 = 7/12$ → $7 + 12 = 19$

### Q13. Mean average precision
Result 1: y y n；Result 2: n n y.

> [!success]- 答案：$5$
> - Result 1：$(1/1 + 2/2)/2 = 1$
> - Result 2：$1/3$
> - mAP $= (1 + 1/3)/2 = 2/3$ → $2 + 3 = 5$

### Q14. PRC plots

| Groundtruth | 0 | 0 | 1 | 0 | 1 | 0 | 1 |
|---|---|---|---|---|---|---|---|
| Likelihood | 35 | 45 | 55 | 65 | 75 | 85 | 95 |

1. Plot two curves: precision vs. likelihood and recall vs. likelihood.
2. Plot PRC.

> [!success]- 答案（P = 3、N = 4）
>
> | 閾值 θ（≥） | 35 | 45 | 55 | 65 | 75 | 85 | 95 | >95 |
> |---|---|---|---|---|---|---|---|---|
> | TP / FP | 3/4 | 3/3 | 3/2 | 2/2 | 2/1 | 1/1 | 1/0 | 0/0 |
> | Precision | 3/7 | 1/2 | 3/5 | 1/2 | 2/3 | 1/2 | 1 | NaN |
> | Recall | 1 | 1 | 1 | 2/3 | 2/3 | 1/3 | 1/3 | 0 |
>
> PRC 的點（recall, precision）：(1/3, 1)、(1/3, 1/2)、(2/3, 2/3)、(2/3, 1/2)、(1, 3/5)、(1, 1/2)、(1, 3/7)。

### Q15. DET/ROC plots
Same dataset as Q14.
1. Plot FNR vs. likelihood and FPR vs. likelihood.
2. Plot DET.
3. Plot ROC.
4. What is the value of auROC?

> [!success]- 答案：auROC = 0.75
>
> | 閾值 θ（≥） | 35 | 45 | 55 | 65 | 75 | 85 | 95 | >95 |
> |---|---|---|---|---|---|---|---|---|
> | FPR | 1 | 3/4 | 1/2 | 1/2 | 1/4 | 1/4 | 0 | 0 |
> | FNR | 0 | 0 | 0 | 1/3 | 1/3 | 2/3 | 2/3 | 1 |
> | TPR | 1 | 1 | 1 | 2/3 | 2/3 | 1/3 | 1/3 | 0 |
>
> - DET 點（FPR, FNR）：(0,1)→(0,2/3)→(1/4,2/3)→(1/4,1/3)→(1/2,1/3)→(1/2,0)→(3/4,0)→(1,0)
> - ROC 點（FPR, TPR）：(0,0)→(0,1/3)→(1/4,1/3)→(1/4,2/3)→(1/2,2/3)→(1/2,1)→(3/4,1)→(1,1)
> - auROC：所有（正例, 負例）配對中，正例分數較高的比例。正例 55 贏 2 個負例、75 贏 3 個、95 贏 4 個 → $9/12 = 0.75$。
