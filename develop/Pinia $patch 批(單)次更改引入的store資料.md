---
date : 2022-05-1209:54
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [Mutating the state](https://pinia.vuejs.org/core-concepts/state.html#mutating-the-state) <br>
Author :: [[@Pinia Doc]] <br>
Topics :: [[-Pinia moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
`$patch`
在元件引入store資料後，可以使用`$patch`對store的資料進行加工:
1. 修改資料內容
```
//官方範例

//引入store的步驟..略

store.$patch({
  counter: store.counter + 1,
  name: 'Abalam',
})

```
2. $patch帶入function進行資料處理
```
//官方範例

cartStore.$patch((state) => {
  state.items.push({ name: 'shoes', quantity: 1 })
  state.hasChanged = true
})

```