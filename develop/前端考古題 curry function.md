---
date : 2022-06-0123:40
aliases : []
---
# Metadata
Status :: #π± <br>
Note Type :: #π¨/π <br>
Source URL :: {θ«ζ PDF URL} <br>
Author :: {PDF/θ«ζεη¨±} <br>
Topics :: [[εη«―θε€ι‘ moc]] <br>
Cover ::

# Evergreen Note

Question :: ιη―ζη« δΈ»θ¦ε¨θͺͺδ»ιΊΌ ?

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