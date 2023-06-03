---
date : 2023-06-0315:27
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [TypeScript - Type Basics](https://www.youtube.com/watch?v=0DzDqtcxnz0&list=PL4cUxeGkcC9gUgr39Q_yD6v-bSyMwKPUI&index=3)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 介紹TS型別概念

---

# Summary 
TypeScript 提供型別檢查，確保變數與函式參數的型別符合預期。例如，一旦變數 `str` 被賦值為字串，再將其賦值為數字就會導致錯誤。另外，也可以在函式參數後定義型別，以避免不適當的參數傳入。

---

# Note

```
let str = 'apple';

str = 123; //出現錯誤提示

str = 'banana';//正常
```

宣告變數時，假設變數`str`已經賦值`'string'`，此時str已被TS認定是字串，如果後續再將`str`復職`123`，則會出現錯誤提示（紅色蚯蚓線），以此類推其他型別。
如果今天使用的是function，我們未將參數定義型別，在調用function時不會出現錯誤提示（紅色蚯蚓線），也可以正常編譯。舉例，這是一個計算圓周的function，`diameter`應該要帶入數字，但我們帶入字串。在瀏覽器執行時得到NAN
```
const circ = (diameter) => {

return diameter * Math.PI;

}

console.log(circ('hello'));
```
為了避免上述錯誤，我們可以將在function內的參數後加上型別定義`: 型別名稱` ，此時hello就會出現錯誤提示（紅色蚯蚓線），TS也不能進行編譯的行為
```
const circ = (diameter: number) => {

return diameter * Math.PI;

}

console.log(circ('hello'));//出現錯誤提示
```