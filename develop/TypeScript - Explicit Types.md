---
date : 2023-06-0315:27
aliases : []
---
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript - Explicit Types](https://youtu.be/__92ek8Xh4o)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 關於 TS 的指定型別


---

# Summary 

---

# Note
TS 會在賦值時定義型別，型別通常會在賦值時自動進行推斷。然而，在某些情況下，我們可能會選擇先行宣告變數，再進行賦值。在這種情境下，我們可能會想要預先定義變數的型別，以確保後續賦值符合我們的預期型別，避免因型別錯誤導致的不可預期問題。
以下是基本定義型別的範例：
```
let price:(number | string);

let array:(string)[];
array.push('eee');//❌ Variable 'array' is used before being assigned.
array = ['aaple','banana'];
```
陣列要注意，如果一開始只是宣告型別但沒有賦值空陣列就使用push修改陣列資料則會出現錯誤訊息"❌ Variable 'array' is used before being assigned."
所以會建議在宣告陣列時就先給他個空陣列
```
let array:(string)[] = [];
let ary:(number | string)[] = [];
ary.push('1111');
ary.push(1111);
```
物件可以定義當前宣告變數為物件或者對物件裡的key進行型別定義，如先前章節所提到的，物件初始值有幾組key value，後續進行資料修改時也需要幾組key value。
```
let obj:object;
obj = {
    age: 11,
    name: 'Ann',
};

let obj2 : {
    age: number,
    name: string,
};

obj2 = {
    age:'11' //❌ Type 'string' is not assignable to type 'number'.
};

obj2 = {
    age:11, //❌  Property 'name' is missing in type '{ age: number; }' but required in type '{ age: number; name: string; }'.
};
```
