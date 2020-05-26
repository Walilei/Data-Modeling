# 1. 解釋名詞
CAP 定理 - 分散式的資料庫系統，無法兼顧以下三點，可參考：[NoSQL介紹](http://garyliutw.blogspot.com/2014/05/mongodb-nosql.html)

* Consistency – 一致性，所有節點訪問同一份最新的數據副本
* Availability – 可用性，每次請求都能得到最新的數據
* Partition tolerance – 分區容錯性，節點間通訊延遲或中斷，仍不影響系統運作

>要一致又有分區容錯，就要有同步時間，影響可用性；要可用性又要分區容錯，就會來不及同步，資料會短暫不一致；要一致性以及可用性，就很難做到分區容錯。

ACID vs BASE - ACID是RDBMS資料交易的特性；BASE是NoSQL資料存取的標準。
* ACID為四項特性的縮寫：
    * Atomic表示交易的原子性，只有全部動作完成才算完成(commit)，否則全部動作取消(rollback)
    * Consistency表示交易從開始前到結束後，均滿足資料完整性，也就是滿足條件拘束、串聯動作、觸發動作
    * Isolation表示隔離性，多個使用者可以同時讀寫，中間過程互不影響
    * Durability持久性表示交易結束後，對數據的修改是永久的，即使系統故障數據也不會丟失

* BASE則代表NoSQL因為無法兼顧CAP原則，取捨過後的三項特性：
    * Basically Available表示基本上讀寫可用，但不保證一致性
    * Soft-State為有跟沒有之間的中介狀態，即狀態可以有一段時間的不同步
    * Eventual consistency最終一致性表示會有短暫不一致，但一定時間後仍會達到一致
***
# 2. NoSQL 資料庫有幾種，課程所提及的 MongoDB, HBase, Redis 又屬於哪一種？
>共分為四種，Key-value利用鍵跟值的搭配來儲存資料，如Redis；Document文件資料庫如mongoDB；Column-family如HBase、Cassandra；Graph圖像式，利用圖學架構來儲存節點關係。
***
# 3. ER Model 設計
參考例題[3-4](https://0rz.tw/iDQj5)
```sh
假設你要替遠距教學的互動功能設計一個系統，該系統記載課程資訊並可讓學生張貼文章到討論版。具體說來，該系統的資料需求如下：
學生 (Student)：包括學號 (sId)、姓名 (name)、性別(sex)、生日 (bDate)、畢業學校 (graduate)、和公司 (employer)。其中畢業學校可能有多個。學號為唯一。
課程 (Course)：包括課程編號 (cId) 和課程名稱(courseName)。其中課程編號為唯一。
老師 (Instructor)：包括老師 ID (iId)、姓名 (name)，和電話 (phone)。老師ID為唯一。
討論版 (Pforum)：包括版名 (pName) 和設立時間 (sDate)。討論版是屬於課程的，換句話說，某一課程的各討論版之版名必定不同。
文章 (Article)：包括流水號 (seq)、主題 (subject)，和內容 (content)。文章是屬於討論版的，換句話說，某一討論版的各文章之流水號必定不同。
此外，老師跟學生間有一個關係型態「修課」(Takes)，老師和課程間有一個關係型態「授課」(Teaches)，學生和文章間有一個關係型態「貼」 (Posts)。請注意我們只需描述現時的資料，不需描述歷史的資料，所以一門課只有一位老師教。
請依以上的需求，畫出ERD。必要的話，可自行假設其他相關狀況，但必須寫清楚。
```


***
# 4. Relational Model 設計
參考例題[4-6](https://0rz.tw/ldeQb)

***
