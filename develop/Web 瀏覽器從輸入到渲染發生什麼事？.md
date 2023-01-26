---
date : 2022-06-0112:32
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️ <br>
Source URL :: [[ECMAScript關鍵30天]] <br>
Author :: [[@yuri]] <br>
Topics :: [[-web運作原理 moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 簡單敘述瀏覽器運作原理

---

# Summary 

---

# Note
1. 瀏覽器會先對使用者輸入的網址做初步的判別，將不合乎ASCII規定的字元進行轉換，接著解析URL，可分析出：通訊協定、網域、路徑
2. 瀏覽器會先透過幾個步驟查找目標網域IP，查找DNS快取、.host檔案，確認沒有IP後才會像DNS server發送請求
3. DNS Server 將IP位址發送給瀏覽器
5. 瀏覽器和target server進行TCP/IP[[三次握手連線]]
7. target server將資料已[[封包]]的形式回傳給瀏覽器
8. 瀏覽器會開始解析封包，HTML-> DOM tree,CSS-> CSSOM tree, JS則是依照`<script>`屬性不同在不同時間點內載入。
9. 瀏覽器將DOM tree套用 CSSOM tree樣式並組成render tree，繪製成Layout模型
10. 頁面繪製完成`<script>`下載的內容執行完畢，瀏覽器進入可互動的狀態，使用者可以操作UI，觸發DOM事件傳遞，並經由[[JS - eventloop]]，處理事件並將結果反應至畫面上