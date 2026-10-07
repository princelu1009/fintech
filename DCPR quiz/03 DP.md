---
tags: [DCPR, quiz, dynamic-programming]
---
# DP (Dynamic Programming)

### Q1. About DP
Which of the following statements about DP (dynamic programming) is/are correct?
1. Every DP problem can be visualized as a path-finding problem.
2. If DP solves a problem, all the subproblems involved in solving the original proglem are also solved.
3. Once the best path is obtained by DP, we can easily derive the second best, the third best, etc., based on the known best path.
4. If you want to obtain the optimal path derived by DP, you can store the back-tracking information along DP iteration to save computation.

> [!success]- 答案：1, 2, 4
> 1. ✅ DP 的狀態與遞迴關係可以畫成一張圖（節點 = 子問題，邊 = 轉移），求最佳解就是在圖上找最佳路徑（如 DTW、edit distance、Viterbi）。
> 2. ✅ DP 是由小到大把所有子問題的最佳解都算出來並存表，所以原問題解完時，過程中的子問題也都解完了。
> 3. ❌ DP 每個節點只保留最佳的那條，第二、第三佳路徑的資訊已經被丟掉，無法「輕易」從最佳路徑推出。要求 k-best 必須修改演算法，在每個節點保留前 k 名。
> 4. ✅ 在遞迴時順便記錄每個節點「從哪裡來」（back-pointer），最後回溯即可得到最佳路徑，不用重算。
