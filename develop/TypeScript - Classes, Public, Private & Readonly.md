---
date : 2023-07-0222:39
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL ::
[TypeScript Tutorial #12 - Classes](https://youtu.be/OsFwOzr3_sE)
[TypeScript Tutorial #13 - Public, Private & Readonly](https://youtu.be/aYmnwDlPB8s)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
Class 就像是藍圖的概念，預先定義了相關的屬性和方法構成物件，後續可以基於Classt創建一個或是多個instance或是繼承該Class衍生出新的子類，物件導向中的繼承：（Inheritance）或是（Polymorphism）
- 繼承：子類（或稱衍生類）繼承了父類（或稱基礎類）的所有屬性和方法，並可以在此基礎上新增或修改屬性和方法。
- 多態：衍生類可以重寫或擴展父類的方法，這樣，當我們對父類和子類的對象調用相同的方法時，它們可以表現出不同的行為。
以下為 TS 中的範例：
```ts
class Invoice {

client: string;

details: string;

amount: number;

  

constructor(client: string, details: string, amount: number) {

this.client = client;

this.details = details;

this.amount = amount;

}

  

format() {

return `${this.client} / ${this.details} / ${this.amount}`;

}

}

  

const invOne = new invoice('nick', 'iphone', 500);

console.log(invOne);
//invoice {client: 'nick', details: 'iphone', amount: 500}
```
當我們建立一個class之後，也可以像之前定義字串陣列型別一樣操作它，限制當前陣列只能使用這個 class 的 instance，例如：
```ts
..... 延續上面定義的invoice


let invoices:invoice[] = [];

invoices.push('a');// ❌ Argument of type 'string' is not assignable to parameter of type 'invoice'.
invoices.push(invOne);

```

class 的屬性或方法前沒有加任何存取修飾符（如 `public`、`private` 或 `protected`），則默認為 `public`，意思是在我們建立 instance 後，可以對內部的屬性和方法進行修改，但**不可以對 type 進行修改**例如：
```ts
..... 延續上面定義的Invoice

// 修改屬性
invOne.client = 'mike';
console.log(invOne) // invoice {client: 'mike', details: 'iphone', amount: 500}

// 修改方法，不建議這麼做，建議改源頭（class) 或是用繼承的方式
invOne.format = function() { return `${this.client} : ${this.details} : ${this.amount}`; };

// 先繼承再修改
class ModifiedInvoice extends Invoice {

format() {

return `${this.client} : ${this.details} : ${this.amount}`;

}

}

// 修改type

```