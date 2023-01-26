---
date : 2022-05-2900:33
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [在物件中 this 的值？](https://ithelp.ithome.com.tw/questions/10194535) <br>
Author :: [[@IT邦]] <br>
Topics ::[[-Javascript moc]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 
1. this 代表函式的綁定物件，通常在函式內執行
2. 不同的程式碼脈絡下，this綁定物件代表不同物件

---

# Tips
- **獨立的function** 當今天this是在function中被調用，等同於全域運行
```js
window.auntie = '漂亮阿姨';
function callAuntie() { console.log('call:', this.auntie);

// this == window 
// 所以此時的 this.auntie 一樣可以取得 window 下的 auntie } 

callAuntie();
```

- **物件的方法** 當今天執行時是object.functionName()，this指向為object
```js
function callName() {
	console.log(this.name);
} 
var name = '全域阿婆';
var auntie = { 
	name: '漂亮阿姨', 
	callName: callName 
	// 這裡的 function 指向全域的 function，但不重要 
} 
callName() // '全域阿婆' 
auntie.callName() // '漂亮阿姨'，呼叫是在物件下調用，那麼 this 則是該物件
```

- **物件的方法2** 當今天將物件內的function存在變數裡，this指向為全域
```js
var name = '全域阿婆';
var auntie = { 
	name: '漂亮阿姨',
	callName: function () {
	  console.log(this.name);
  } 
}
// 將 function 指向物件內的 function，不過不重要
callThisName = auntie.callName;
callThisName()// '全域阿婆'

```

- **事件處理函式的this** 當今天為DOM搭配eventListener，this指向為觸發事件的對象
```js
var elements = document.getElementsByTagName('div');
function changeDOM() {
	console.log(this);
	// 指向當前的 DOM this.style.border = '1px solid red' 
}
for (var i = 0; i < elements.length; i++) { elements[i].addEventListener('click', changeDOM, false); 
}

```
- **建構函式this** 當今天是使用new創建，this指向為當前物件本身
```js
function FamilyConstructor () { 
	this.mom = '老媽' 
} 
var myFamily = new FamilyConstructor();
console.log(myFamily.mom);
```
- **箭頭函式this** 箭頭函式沒有自己的this，執行時決定this指向誰


---
# Note
this的指向是在運行時決定的(runtime binding)與函式在何處宣告無關，而是取決於函式被呼叫的方式以及地點。
this的指向分成：window,function,eval(被淘汰的用法)