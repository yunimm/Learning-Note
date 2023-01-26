---
date : 2022-05-3120:14
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [Day5 [JavaScript 基礎] Event Loop 機制](https://ithelp.ithome.com.tw/articles/10214017) <br>
Author :: [[@IT邦]] <br>
Topics :: [[-Javascript moc]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# How to use
![[Pasted image 20220531211625.png]]
![[Pasted image 20220531211159.png]]

---

# Note
eventloop是js的運行機制，負責監控stack和taskQueuq，如果今天stack為空，則拉taskQueuq的callback function去stack執行，解決了js單執行緒造成block的狀況。
詳細說明:
js執行的任務分成兩種，1.同步任務2.非同步任務，那如果今天沒有eventloop，只有js運行這些任務，會造成卡頓，例如：
```js
console.log('你好啊')
setTimeout(function cb(){
	console.log('很好')	
},5000)
console.log('最後一行')
```
js會循序執行，執行到setTimeout時，就會至少等五秒再印出內容，接著執行下一段程式碼，
那因為這關係到用戶體驗，所以使用者可能會認為網頁壞了...?
為了不讓js程式碼block，於是有了eventloop。

以上一段程式碼為例，執行第一行，第二行js遇到setTimeout時，會先將setTimeout拉到旁邊，執行setTimeout，將setTimeout裡的callback function丟進taskQueuq，繼續執行第三行，等第三行執行完畢，eventloop會將taskQueuq的callback function拉進stack運行

