---
date : 2022-06-0116:39
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: <br />
[Closures in JS 🔥 | Namaste JavaScript Episode 10](https://www.youtube.com/watch?v=qikxEIxsXco&t=275s) <br />
[ExplaninThis](https://www.explainthis.io/zh-hant/interview-guides/javascript/what-is-closure)<br>

Author :: [[@Akshay Saini]]  [[@ExplanThis]]<br>
Topics :: [[JavaScript MOC]] <br>
# Evergreen Note

Question :: 這部教學主要在說什麼 ?

Answer :: 深入淺出閉包的概念、原理、用法
- [x] [理解閉包基本概念 ](https://youtu.be/qikxEIxsXco?t=675)
- [x] [理解閉包應用 ](https://pjchender.blogspot.com/2017/05/javascript-closure.html)
- [ ] 理解閉包進階用法
---

# Summary 
閉包是什麼：宣告function時，function對其詞法環境綁定(記住了宣告時的作用域環境)，使得內層function可以引用外部變數，並且記住這個變數。因為能夠記住這個外部變數，閉包很常被用來做狀態保存。
閉包的應用：
- 狀態保存：例如React中的`useState` 模擬一個簡化版的 `useState` :
```javascript
function useState(initState) {
	let state = initState;
	
	function getState(){
		return state;
	}
	function setState(updateState) {
		state = updateState;
	}

	return [getState, setState];
}
const [count, setCount] = useState(3);

count();//3
setState(5);//5

```
- 變數私有化 : 有時候我們在開發時，有些變數並不想讓外部來存取，所以需要變數私有化的方法但JS並不支援變數私有化，我們可以透過閉包的方式做出類似的功能：
```javascript
// privateCounter 沒被法被外部修改
// 因為閉包的關係 increment 與 decrement 可以存取到 privateCounter
// 因此 privateCounter 只能夠透過 increment 與 decrement 來改，這能有效避免被誤觸到
const counter = (function() {
  let privateCounter = 0;

  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    },
  }
})();

console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1
```
- 緩存機制：一般函數的詞法環境在函數返回後就被銷毀，但是閉包會保存對創建時所在詞法環境的引用，即便創建時所在的執行上下文被銷毀，但創建時所在詞法環境依然存在，以達到延長變量的生命週期的目的。
  [範例1](https://hackmd.io/@wheat0120/javascript-memoization)
```javascript
function getTool(todoTask) {
  const doneCache = {};
  return function (){
    const taskContent = JSON.stringify(arguments);

    if(doneCache[taskContent]) {
      return doneCache[taskContent];
    } else {
      const taskResult = todoTask.apply(this,arguments);
      doneCache[taskContent] = taskResult;
      return taskResult;
    }
  }
};

const work = getTool((task) => {
    console.log('前往倉庫拿工具')
    return task + ': 已完成工作'
})


console.log('Day1', work('修理馬桶'));
console.log('Day2', work('修理馬桶'));
console.log('Day3', work('修理屋頂'));

```
[範例2](https://www.explainthis.io/zh-hant/interview-guides/javascript-whiteboard/cache-function)
不確定會帶入幾個參數，可以使用展開運算子的寫法，會將數組轉換成參數
``` javascript
let args = [1, 2, 3];

function add(a, b, c) {
  return a + b + c;
}

console.log(add(...args)); // Output: 6

```

``` javascript
function cached(fn) {
  // 聲明一個 cache 物件，透過 cache 來放緩存的東西
  // 因為閉包的緣故，下面回傳的函式可以存取到這個 cache 變數
  const cache = {};

  // 透過擴展運算符，拿到引數
  return (...args) => {
    // 將引述當作緩存的 key
    const key = JSON.stringify(args);
    // 查看現在的緩存有沒有這個 key，有的話就不用再算，直接回傳
    if (key in cache) {
      return cache[key];
    } else {
      // 沒有的話，就把收到引數帶入，運算出結果
      const val = fn(...args);
      // 把結果放入緩存，下次有同樣的 key 就不用重新運算
      cache[key] = val;
      return val;
    }
  };
}
```
閉包的缺點：
- 內存泄露

---

# Note

範例一：
```js
function outer() {
	const x = 10
	function inner() {
		console.log(x)
	}
	return inner
}
const z = outer()
console.log(z)
z()
```

範例二，
1. 在全域建立名為dogHouse的function
2. 將數字0存在變數count
3. return 一個匿名function，帶入參數name，當function被執行count+1並印出count name字串
4. 在全域建立dogCount的常數，將dogHouse function賦值給它
5. 執行dogCount並帶入參數dog字串

```js

function dogHouse () {
	let count = 0;
	return (name) => {
	count += 1;
	console.log(`${count}${name}`);
	};
};

const dogCount = dogHouse()

dogCount('dog'); //1dog
dogCount('dog');//2dog
dogCount('dog');//3dog

const catCount = dogHouse()

catCount('cat'); //1cat
catCount('cat');//2cat
catCount('cat');//3cat
```
步驟五帶入的字串對應return的匿名function的參數，如果今天是在dogHouse function 帶入參數則...

```js
function dogHouse (name) {
	let count = 0;
	return () => {
	count += 1
	console.log(`${count}${name}`)
	};
};

const dogCount = dogHouse('dog')

dogCount()
dogCount()
dogCount()
```



