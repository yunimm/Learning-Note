---
date : 2022-06-0123:40
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/🗞 <br>
Source URL :: {論文 PDF URL} <br>
Author :: {PDF/論文名稱} <br>
Topics :: [[前端考古題 moc]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Question
```js
add(1, 2); // 3
add(1)(2); // 3
```

---

# Solution
```js
function add (x, y) {
  if (arguments.length === 1) {
    return function (y) {
      return x + y;
    }  
  }
  return x + y;
}
```