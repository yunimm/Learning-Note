---
date : 2023-03-2723:07
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: {教學 URL} <br>
Author :: The Complete Node.js Developer Course (3rd Edition) <br>
Topics :: [[-Node.js moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
##### 章節2
介紹Node.js和瀏覽器語法差別和底層運作原理

---

# Note
#### 章節2
##### 底層運作原理
![[截圖 2023-03-27 下午11.10.25.png]]
chrome/node底層都是v8引擎,而v8是使用c++寫的
圖左可以看到`localStorage.getItem` 和 `document.querySelector`都不是JS的語法，是瀏覽器提供的語法，圖右可以看到`fs.readFile` 和 `os.platform` 是 node提供的語法，但兩者的底層都是透過C++完成的。

##### 範例測試
實際打開瀏覽器的開發者工具和terimal，當你在瀏覽器輸入`window`，會看到methods和property，當你在terimal輸入則沒有`window`這項指令，node是`global` 。當你在瀏覽器輸入`document`，會印出DOM節點，node輸入`process` 。
browser : ` window,` `document`
node :` global`, `process`

##### 為什麼要使用node.js
1. node.js採用non-blocking I/O
   I/O : input, outpt  ex: querying a database to fetch some records for a given user.
2.
為什麼none-block是重點？因為在等待資料回應時，可以繼續執行其他程式碼並發出請求

