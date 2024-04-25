---
date : 2023-01-0922:36
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [nodejs中的文件系统](https://www.cnblogs.com/flydean/p/14290004.html#fsstat%E6%96%87%E4%BB%B6%E7%8A%B6%E6%80%81%E4%BF%A1%E6%81%AF)<br>
Author :: {作者名稱} <br>
Topics :: [[Node.js MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# How to use

---

# Note

看教學[[astro + TS 實作部落格]]發現這個用法的，在這之前沒使用過node.js搭配js..
以教學的情境來說，我在文章Layout中設置顯示圖片，但其中一篇文章並沒有圖片，但頁面上就會破圖，為了避免這個情況，使用了node.js的語法`fs.promise.stat`判斷當前有沒有這個檔案，如果存在`true` 不存在 `false`
