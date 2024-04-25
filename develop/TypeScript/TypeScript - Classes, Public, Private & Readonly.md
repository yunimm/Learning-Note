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
Topics :: [[TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
#### 什麼是class ?
class 就像是藍圖的概念，預先定義了相關的屬性和方法構成物件，後續可以基於 class 創建一個或是多個instance 或是繼承該 class 衍生出新的子類，物件導向中的繼承：（Inheritance）或是（Polymorphism）
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

console.log(invOne);//invoice {client: 'nick', details: 'iphone', amount: 500}
```
當我們建立一個class之後，也可以像之前定義字串陣列型別一樣操作它，限制當前陣列只能使用這個 class 的 instance，例如：
```ts
..... 延續上面定義的invoice


let invoices:invoice[] = [];

invoices.push('a');// ❌ Argument of type 'string' is not assignable to parameter of type 'invoice'.
invoices.push(invOne);

```

#### class 存取修飾符（Access Modifiers）
##### public
class 的屬性或方法前沒有加任何Access Modifiers（如 `public`、`private` 或 `protected`），則默認為 `public`，意思是在我們建立 instance 後，可以對內部的屬性和方法進行修改，但**不可以對 type 進行修改**例如：
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

// 修改type，塞入原本沒定義的型別
invOne.client = 1111; // ❌ Type 'number' is not assignable to type 'string'.

```
##### private
當我們在屬性上加上了`private`，該屬性只能在 class 內訪問，class 外(包含子類別)不能夠直接訪問和修改
```ts
class Invoice {

	private client: string;
	
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

console.log(invOne.client); // ❌ Property 'client' is private and only accessible within class 'Invoice'.
invOne.client = 'aaa'; // ❌ Property 'client' is private and only accessible

//workaround 
console.log(invOne["client"]);
invOne["client"] = "HARU";
```
**什麼情況需要設置 `private` ？**
在物件導向程式設計中，`private` 關鍵字是用來封裝類別內部的狀態和實作細節，以下列舉幾種可能需要設定 `private` 的情況：
1. **保護敏感資訊**：如果類別包含了一些敏感或者重要的資訊，例如用戶密碼，資料庫連線等，這些資訊可能不應該在類別的外部被直接訪問或修改，此時可以將這些屬性設為 `private`。
    
2. **維護物件內部狀態的一致性**：有些情況下，你可能希望一個類別的內部狀態需要維護某種一致性或者符合某種規則。例如，你可能有一個 `BankAccount` 類別，該類別有一個 `balance` 屬性表示帳戶餘額，你可能不希望餘額可以被隨意修改，而是通過 `deposit` 和 `withdraw` 方法來控制。此時可以將 `balance` 屬性設為 `private`，並提供公開的方法來改變它。
    
3. **隱藏實作細節**：有些類別的內部實作可能相當複雜，包含了大量只有在類別內部使用的輔助方法和屬性。這些內部實作細節對於使用該類別的程式設計師來說可能是無關緊要的，甚至可能會引起混淆。為了使類別的接口（API）更加清晰和易於使用，可以將這些內部使用的方法和屬性設為 `private`。
    
總的來說，`private` 的使用可以幫助我們設計出更加穩健、安全和易於使用的類別。

##### readonly
當我們在屬性上加上了`readonly`，該屬性只能在類別的構造器中初始化，一旦初始化後就不能再修改（immutable objects）。
```ts
class invoice {

	readonly client: string;
	
	details: string;
	
	amount: number;
	
	  
	
	constructor(client: string, details: string, amount: number) {
	
		this.client = client;
		
		this.details = details;
		
		this.amount = amount;
	
	}
	
	format() {
		this.client = 'apple'; // ❌ Cannot assign to 'client' because it is a read-only
		return `${this.client} / ${this.details} / ${this.amount}`;
	
	}

}

const invOne = new invoice('nick', 'iphone', 500);
invOne.client = 'aaa'; // ❌ Cannot assign to 'client' because it is a read-only property.
```
當我們有定義 Access Modifiers 時可以直接將 Access Modifiers 寫在 constructor 內，會自動為你創建並初始化一個對應的 instance 成員：
```ts
class invoice {
	//readonly client: string;
	
	//public details: string;
	
	//public amount: number;
	
	constructor(
		
		readonly client: string,
		
		public details: string,
		
		public amount: number) {
	
	}
	
	  
	format() {
	
		return `${this.client} / ${this.details} / ${this.amount}`;
	
	}

}
```

#### 補充資料
##### ES10的private fields #
JavaScript 並不直接支援私有function（private methods）的概念，這和 Java 等其他物件導向程式語言是有所不同的。JavaScript 的函數和方法預設都是公開的，可以在類別的外部被調用。
JavaScript 直到 ES2019 (即 ES10) 才加入了私有欄位（private fields）的概念，可以用於實現類別的私有方法。在這之前，JavaScript 並沒有內建的方式來限制函數或變數的可見度。然而，開發者可以通過特定的設計模式（例如模組模式或閉包）來實現一種類似私有變數或函數的效果。我們可以在屬性或方法名稱前加上一個 `#` 符號，將它們標記為私有的。私有欄位只能在其所屬的類別中被訪問或修改，不能從類別的實例或子類別中訪問。例如：
```js
class MyClass {
  #privateMethod() {
    console.log('Hello from private method');
  }

  callPrivateMethod() {
    this.#privateMethod();
  }
}

const myInstance = new MyClass();
myInstance.callPrivateMethod(); // Prints: "Hello from private method"
myInstance.#privateMethod(); // SyntaxError

```
##### private 和 private fields 差異

#### 參考資料
- [TS 存取 private workaround方式來源](https://www.tpisoftware.com/tpu/articleDetails/2017)
- [### [料理佳餚] 拐個彎的 JavaScript 的私有欄位（Private Field）](https://dotblogs.com.tw/supershowwei/2020/10/12/131655)