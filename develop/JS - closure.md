---
date : 2022-06-0116:39
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [Closures in JS 🔥 | Namaste JavaScript Episode 10](https://www.youtube.com/watch?v=qikxEIxsXco&t=275s) <br>
Author :: [[@Akshay Saini]] <br>
Topics :: [[-Javascript moc]] <br>
Cover ::

# Evergreen Note

Question :: 這部教學主要在說什麼 ?

Answer :: 深入淺出閉包的概念、原理、用法
- [x] [理解閉包基本概念 ](https://youtu.be/qikxEIxsXco?t=675)
- [x] [理解閉包應用 ](https://pjchender.blogspot.com/2017/05/javascript-closure.html)
- [ ] 理解閉包進階用法
---

# Summary 
宣告function時，function對其詞法環境綁定(記住了宣告時的作用域環境)，使得內層function可以引用外層functiton變數就是閉包的概念

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



