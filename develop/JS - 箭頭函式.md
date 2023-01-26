---
date : 2022-10-2816:42
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL ::[[JS] 箭頭函式（arrow function）和它對 this 的影響](https://pjchender.dev/javascript/js-arrow-function/)<br>
Author :: {作者名稱} <br>
Topics :: [[-Javascript moc]] <br>
補充資料 ::[# [JavaScript 教學 - ES6] Arrow Function 箭頭函式， 還有Arrow function 要注意的事！](https://www.youtube.com/watch?v=C4DTfP-7VyE)

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 
1. 箭頭函式解決什麼問題？
	- 讓語法更簡潔
	- 不同的程式碼脈絡下，this綁定物件代表不同物件
2. 箭頭函式的特點？
	- 定義時決定this的指向，不會隨著使用的脈絡而改變
3. 箭頭函式的缺點？
	   - 不支援物件的method，只能用function寫法
	   - 不能作為物件建構子（constructor）使用
---

# How to use

---

# Note
[範例出處](https://askie.today/this-arrow-function-in-javascript/)
箭頭函式this範例：
```js
let BMI = {
  test: function () {
    console.log('BMI.test', this)
    function testtest () {
      console.log('BMI.test > testtest(ES5)', this) 
    }

    let testtest2 = () => {
      console.log('BMI.test > testtest2(ES6)',this)
    }

  testtest()
  testtest2()

  },
  test2: () => {
    console.log('BMI.test2', this)
  }
}

BMI.test()
BMI.test2()
```

判斷方法：
es5:
看呼叫時是誰呼叫的，如果沒有物件的情況下就會一層一層往外找到window。
es6:
大部分情況都是指向windows。如果被ES5函式包住，則this就是指向包他的function，如上方範例，testtest2外面有個ES5匿名function包住他，所以印出結果是{test: ƒ, test2: ƒ}。下方test2沒有被包住，所以指向window。
