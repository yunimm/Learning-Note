---
date : 2022-05-3007:06
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL ::[我知道你懂 hoisting，可是你了解到多深？](https://blog.techbridge.cc/2018/11/10/javascript-hoisting/) <br>
Author :: [[@huli]]<br>
Topics :: [[JavaScript MOC]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 關於hotsing

---

# Note
為什麼需要hoisting? 反過來想，如果沒有hoisting會怎樣?
1. 一定要宣告變數才能使用變數，沒差
2. 一定要宣告function才能使用function，有差，這樣必須把所有function都寫在檔案上面，很麻煩
3. 沒有辦法在function裡呼叫另一個function
### var
如果使用var,會發現var有一個特性，hoising。

什麼是hoisting ? 執行程式碼時，變數的宣告被提升到前面了
```js
console.log(a)
var a = 10

//結果為undefined
```
這段程式碼可以拆解為：
```js
var a //宣告變數	
console.log(a) //印出a
a = 10 //將10賦值給a
```
### var + arrow function  + function
如果使用var 宣告 arrow function 則會印出undefined，同理如果將function賦值給變數，一樣沒有
```js
console.log(test)//undefined
console.log(testB)//undefined
var test = () => {
	console.log('TEST')
}
var testB = funtion() {
	console.log('TEST')
}
```
### function 
```js
console.log(getName)//f gatName
function getName() {

}
```
如果變數宣告遇到function，function的優先層級大於宣告變數，function參數又大於function
```js
function test(val) {
  console.log(val)
  var val = 10
}
test(100)
//印出結果為100
```
這段程式碼可以拆解為：
```js
function test(val) {
  var val //function裡的變數宣告
  var val
  console.log(val)
  val = 10
  val = 100//function裡的變數值
}
```
### let , const
let和const也有hoisting，差別在於var會在宣告變數後將變數初始化為`undefined`
let和const則是在==提升之後==、==賦值之前==，存取會出現TDZ(Temporal Dead Zone)


