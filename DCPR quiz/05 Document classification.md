---
tags: [DCPR, quiz, document-classification, NLP]
---
# Document classification

> [!note] TF-IDF 公式（本筆記採用）
> $\text{tf}(t,d) = \dfrac{t \text{ 在 } d \text{ 出現次數}}{d \text{ 的總詞數}}$，$\text{idf}(t) = \log\dfrac{N}{\text{df}(t)}$，$\text{tf-idf} = \text{tf}\times\text{idf}$
> $N$ = 文件數，df = 含有該詞的文件數。

文件集合（Q1、Q2 共用）：
- Doc 1: CDBDA
- Doc 2: CA
- Doc 3: ACADA
- Doc 4: CDB
- Doc 5: ACCA

### Q1. TF-IDF
Given a collection of 5 documents with 4 tokens (or words), as shown above. Answer the following questions.
1. What is their TF-IDF?
2. Which token(s) is/are useless for classification? Why?

> [!success]- 答案
> df：A=4、B=2、C=5、D=3。idf（log10）：A=0.0969、B=0.3979、C=0、D=0.2218。
>
> | token | Doc1 | Doc2 | Doc3 | Doc4 | Doc5 |
> |---|---|---|---|---|---|
> | A | 0.0194 | 0.0485 | 0.0581 | 0 | 0.0485 |
> | B | 0.0796 | 0 | 0 | 0.1326 | 0 |
> | C | 0 | 0 | 0 | 0 | 0 |
> | D | 0.0887 | 0 | 0.0444 | 0.0739 | 0 |
>
> （若用自然對數 ln，每個值乘上 2.3026。）
>
> 2. **C 沒有用**：C 出現在每一份文件，$\text{idf} = \log(5/5) = 0$，TF-IDF 全為 0，無法區分文件。

### Q2. TF-IDF (log base 10)
Answer the following questions (assuming the "log" in the formula of TF-IDF is based on 10).
1. What is the TF-IDF vector of token B?
2. What is the TF-IDF vector of token C?

Format: round each element to four decimal places unless it is 0, such as "[0 0.3821 0 0 0.2187]".

> [!success]- 答案：B = [0.0796 0 0 0.1326 0]、C = [0 0 0 0 0]
> B 出現在 Doc1（1/5）與 Doc4（1/3），$\text{idf}=\log_{10}(5/2)=0.3979$：
> $0.2\times0.3979 = 0.0796$，$\frac13\times 0.3979 = 0.1326$。
> C 每份文件都有，idf = 0。

### Q3. 白癡造句法
請用下列詞來進行白癡造句。
1. 台大
2. 文筆
3. 表現
4. 天花

> [!success]- 參考答案
> 「白癡造句」是讓目標詞的字跨在兩個詞中間，用來說明斷詞的歧義問題：
> 1. 台大：這個平**台大**家都在用。（平台／大家）
> 2. 文筆：我在整理論**文筆**記。（論文／筆記）
> 3. 表現：我看了手**表現**在是三點。（手表／現在）
> 4. 天花：我今**天花**了很多錢。（今天／花了）
>
> 重點：若只靠詞庫比對，這些句子都可能被斷錯。

### Q4. 使用詞庫進行斷詞的優點和缺點
我們可以利用詞庫來進行斷詞，請舉出此方法的一個優點和一個缺點。

> [!success]- 參考答案
> - 優點：方法簡單、速度快，不需要標記好的訓練語料。
> - 缺點：無法處理詞庫沒有的新詞（未知詞，OOV，如人名、新流行語），也難以解決歧義（如「白癡造句」的例子），效果受詞庫品質影響很大。

### Q5. Chinese word segmentation by dictionary
利用詞庫來進行斷詞，最常用到的兩種方法是？

> [!success]- 答案：正向最大比對法、反向（逆向）最大比對法
> Forward / backward maximum matching：從句首（或句尾）開始，每次取詞庫中能比對到的**最長詞**，切下後繼續處理剩下的部分。

### Q6. Chinese word segmentation
請以正向及反向的「最大比對法」來進行下列文句的斷詞。（假設詞庫的最長詞為四個字。）
1. 話不投機會很無聊
2. 不可以營利為目的

> [!success]- 參考答案（假設詞庫含：話不投機、投機、機會、無聊、不可、不可以、可以、營利、目的）
> **1. 話不投機會很無聊**
> - 正向：話不投機／會／很／無聊（先取到四字詞「話不投機」，正確）
> - 反向：從句尾取「無聊」→「很」→「機會」→「投」→「不」→「話」：話／不／投／機會／很／無聊（錯誤）
>
> **2. 不可以營利為目的**
> - 正向：不可以／營利／為／目的
> - 反向：目的／為／營利／不可以 → 不可以／營利／為／目的
> - 正確應為「不可／以營利為目的」（不可／以／營利／為／目的）。兩種方法都會因為「不可以」在詞庫裡而斷錯，說明最大比對法無法處理這類歧義。
>
> ⚠️ 實際結果取決於題目假設的詞庫內容。
