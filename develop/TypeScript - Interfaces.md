---
date : 2023-07-0323:37
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #15 - Interfaces](https://youtu.be/VbW6vWTaHOY)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
#### 什麼是 Interface ?
TypeScript 中的 `interface` 主要是用於描述複雜的資料結構，並且增強了程式碼的可重用性。它讓我們可以創建一種新的名稱，用於描述可能具有多個屬性和方法的物件結構與基本型別註記相比，`interface` 提供了一種方式，讓我們可以定義並重用更複雜的結構，對於開發大型或者結構複雜的專案非常有用。
```ts
interface Point {
  x: number;
  y: number;
}

function drawPoint(pt: Point) {
  //...
}

drawPoint({x: 3, y: 4});

```
在這個例子中，Point interface 描述了一個物件必須有 x 和 y 兩個數字型別的屬性。當我們嘗試傳遞一個物件給 drawPoint 函式時，TypeScript 會檢查該物件是否符合 Point interface 的結構，如果不符合就會在編譯時報錯。使得開發者可以在編碼階段就能知道物件的結構，而不是等到運行時才發現錯誤。因此，大大提高了程式碼的可讀性和維護性。
#### interface 和 class 的差異？
`interface` 和 `class` 在 TypeScript 中都是用於描述物件的結構和型別的工具，但是它們的用途和行為有一些關鍵性的差異：

1. **定義方式**：`interface` 主要用來定義物件的形狀（物件的結構），並不能生成實例，也不能包含實現邏輯（例如函數的具體實現）。`class` 則不同，它既能定義物件的形狀，也能生成實例，並且可以包含具體的實現邏輯。
    
2. **實現與繼承**：`class` 可以實現（implements）一個或多個 `interface`，這表示該 `class` 必須符合這些 `interface` 定義的結構。同時，`class` 也可以繼承（extends）其他 `class`，這表示該 `class` 繼承了父 `class` 的屬性和方法。而 `interface` 只能被 `class` 實現，或者被其他 `interface` 繼承。
    
3. **物件導向特性**：`class` 支持物件導向程式設計的特性，如繼承（inheritance）、封裝（encapsulation）、多態（polymorphism）。而 Interface 則沒有這些特性，它只是一種描述物件結構的工具。
    

簡單來說，你可以將 Interface 看作是一種更輕量級、更靈活的 Class，它可以幫助你在編碼階段就定義和檢查物件的結構，從而提高程式碼的可讀性和維護性。而 Class 則提供了更多的物件導向程式設計的特性和功能，適用於較大或更複雜的專案。

#### Interface 使用範例
假設我預期我有個名為`person`的物件，我先定義好他的參數型別和方法，之後使用`person`時就必須按照`Interface` 的定義開發：
```ts
interface IsPerson {
	name: string;
	age: number;
	speak(a: string): void;
	spend(a: number): number;
}

const me:IsPerson = {
	name: 'Nick',
	age: 28,
	speak(text: string): void {
		console.log(text)
	},
	spend(amount: number): number {
		console.log(`I spent ${ amount }`)
		return amount;
	},
}

console.log(me);//{name: 'Nick', age: 28, speak: ƒ, spend: ƒ}

```
如果我把`spend`拿掉，這時TS就會在編譯前提醒你有錯：
```ts
const me:IsPerson = {
	name: 'Nick',
	age: 28,
	speak(text: string): void {
		console.log(text)
	},
	//spend(amount: number): number {
	//	console.log(`I spent ${ amount }`)
	//	return amount;
	//},
	// ❌ Property 'spend' is missing in type '{ name: string; age: number; speak(text: string): void; }' but required in type 'IsPerson'.
}

```
同樣的，如果我新增了一個方法/屬性，一樣會報錯：
```ts
const me:IsPerson = {
	name: 'Nick',
	age: 28,
	speak(text: string): void {
		console.log(text)
	},
	spend(amount: number): number {
		console.log(`I spent ${ amount }`)
		return amount;
	},
	sing(text: string):void {
		console.log(text)
	},
	// ❌ Type '{ name: string; age: number; speak(text: string): void; spend(amount: number): number; sing(text: string): void; }' is not assignable to type 'IsPerson'. Object literal may only specify known properties, and 'sing' does not exist in type 'IsPerson'.
}

```
先前提到`interface` 的其中一個優點是重用性，我們已經定義好了名為 `IsPerson` 的` interface` ，我們可以這樣使用它：
```ts
1.宣告變數時，一眼就可以知道這個變數儲存的資料結構長怎樣，不用一層一層去追
let someone:IsPerson;

2.當作 function 的參數型別傳入，IDE會自動推論你要帶入的Key
const greetPerson = (person: IsPerson) => {
	console.log(person.)
}
2.1 呼叫 function 時會提醒你不要亂塞參數

```
![[截圖 2023-07-04 上午12.12.03.png]]