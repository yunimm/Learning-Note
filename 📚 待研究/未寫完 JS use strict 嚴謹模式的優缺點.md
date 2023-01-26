---
date : 2022-05-3009:31
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: {文章 URL} <br>
Author :: {作者名稱} <br>
Topics :: [[未寫完 JS use strict 嚴謹模式的優缺點]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# How to use
在開頭加上`"use strict"`,在function第一行加上`"use strict"`
```js
"use strict"
x = 3.14 //error
```
```js
function getID() {
  "use strict"
  y = 3.14 //error
}
```

---

# Note
目的：解決JS一些不合理、不嚴謹的部分、提高編譯效率，增加運行效率，在不穩定的語法或妨礙最佳化的語意都會跳出警告，讓開發者避開這些寫法。
- 要先宣告才能使用變數
- 不允許刪除變數或物件
- 不允許刪除函式
- 不允許變數名稱重複
- 不允許使用八進制
- 