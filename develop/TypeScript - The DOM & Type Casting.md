---
date : 2023-07-0122:38
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #11 - The DOM & Type Casting](https://youtu.be/hcuKd-Q_tP8)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: DOM的型別判斷

---

# Summary 

---

# Note
當怎麼用 TS 定義 DOM 型別？
- 這樣寫沒有問題，TS 也會自動幫你推論型別，
![[截圖 2023-07-01 下午10.47.34.png]]
```ts
const arc = document.querySelector('a');
console.log(arc);
```
- 那這樣呢？如果我們要取得 `<a>`  的 href
```ts
const arc = document.querySelector('a');
console.log(arc.href); // TS 報錯 'arc' is possibly 'null'.ts(18047)

```
  因為我們沒有考慮到 null 的情況，所以 TS 噴錯了
  這時候可以這麼改：
  1.  加上驚嘆號 (Non-null assertion operator)，代表我確定這個變數不會是 `null` 或 `undefined`，所以不需要進行空值檢查”
  2. 使用 `Optional Chaining` 如果 `arc` 是 `null` 或 `undefined`，則整個表達式將立即返回 `undefined`，而不會嘗試訪問 `href` 屬性。這可以防止當 `arc` 為 `null` 或 `undefined` 時出現不能讀取 `null` 或 `undefined` 的屬性值的錯誤。
  3. 做防呆
```ts
1.
const arc = document.querySelector('a')!;
console.log(arc.href);

2. 
const arc = document.querySelector('a');
console.log(arc?.href);

3.
const arc = document.querySelector('a');

if (arc) {

console.log(arc.href);

}

```
- 如果我們今天是抓取Dom的class name
```ts
const form = document.querySelector('.new-item-form');

console.log(form);

```
  此時會發現form自動推論的型別並不是 `HTMLFormElement`
	![[截圖 2023-07-02 下午4.23.09.png]]
	這時候我們可以用 `as` **Type Assertions(型別斷言)** 來強制定義當前form的型別是 `HTMLFormElement`
	[官方文件Type Assertions(型別斷言)](https://www.typescriptlang.org/zh/docs/handbook/2/everyday-types.html#type-assertions)
	```
```ts
const form = document.querySelector('.new-item-form') as HTMLFormElement;

console.log(form);

console.log(form.children);
```


