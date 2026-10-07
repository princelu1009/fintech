---
tags: [DCPR, quiz, clustering]
---
# Clustering

### Q1. About K-means Clustering
Which of the following statements about k-means clustering are correct?
1. To initiate k-means clustering, you need either an initial set of cluster centers or an initial partitioning of the dataset.
2. The iterative procedure in k-means clustering is guaranteed to convergence.
3. K-means clustering is based on the concept of coordinate optimization.
4. K-means clustering can reduce the dimensionality of a dataset.
5. K-means clustering is an example of unsupervised learning.

> [!success]- 答案：1, 2, 3, 5
> 1. ✅ 起始可以給 k 個中心，或給一個初始分群（再算出中心），兩者擇一。
> 2. ✅ 每一步（重新分群、更新中心）都不會讓目標函數（各點到中心的距離平方和）變大，且分群方式有限，所以一定收斂（但只保證到 local minimum）。
> 3. ✅ 固定中心最佳化分群、固定分群最佳化中心，輪流進行，就是 coordinate optimization。
> 4. ❌ k-means 是減少「資料筆數」（用 k 個中心代表所有資料，data reduction / vector quantization），不是降低「維度」。降維是 PCA、LDA 的工作。
> 5. ✅ 不需要標籤，屬於非監督式學習。
