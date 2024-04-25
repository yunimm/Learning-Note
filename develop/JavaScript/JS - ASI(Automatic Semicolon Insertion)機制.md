---
date : 2023-01-2623:40
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️ <br>
Author :: [[＠卡斯伯]] <br>
Topics :: [[JavaScript MOC]]<br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 說明ASI執行的條件以及優缺點

---

# Summary 
執行條件：
- 程式碼開頭為 `(` `[` `/`  前一行斷行不會加入分號，有可能會出錯，而無法運行
- 程式碼開頭為 `+` `-` `*` `/` `,` `.` 前一行斷行不會加入分號，不會出錯，但有可能會造成運算不如預期
優點：程式碼簡潔，一種codingStyle風格(standard)
缺點：如果使用不當，容易造成開發者debug困難
解決方案：在結尾加入`;` 或是在`(` `[` `/`  前方補上 `;`

---

# Note

