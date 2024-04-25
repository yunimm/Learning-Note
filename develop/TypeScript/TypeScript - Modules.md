---
date : 2023-07-0320:06
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #14 - Modules](https://youtu.be/EpOPR03z4Vw)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
#### 關於 TS Module 
隨著專案規模增長，可能會需要將程式碼進行模組化，例如拆成 DOM 交互行為、Fetch API、Auth等等，不同檔案，方便後續好擴充和維護。在 JS ES6 時新增了 module system 的支援，同樣的 TS 也同樣支援這個特性，並且加入了一些額外的功能，例如類型檢查和自動完成。要注意的是，JS 和 TS 的 module system（ES6 的 `import` 和 `export` 語法）本身並不被所有的瀏覽器支援，尤其是舊版的瀏覽器。然而，我們可以使用如 Webpack 和 Babel 這樣的工具，將使用了這些新特性的程式碼轉換（或稱為「轉譯」、「編譯」）成舊版瀏覽器可以理解和執行的程式碼。這種轉換過程常常被稱為「下轉譯」（Down-Transpiling）或「轉譯」（Transpiling）。
##### 如果今天沒有使用打包工具，我們該如何設定 tsconfig ? 
```ts
//tsconfig.ts

"target": "es6", // 指定編譯生成的JS版本: 'ES3' (default), 'ES5', 'ES6'/'ES2015', 'ES2016', 'ES2017', or 'ESNEXT'
"module": "es2015" //指定生成哪種模組: 'commonjs', 'amd', 'system', 'umd' or 'es2015'

```
```HTML
//index.html

// script tpye 加上 module
<script type="module" src="app.js"></script>
```
在 `src`  建立資料夾，資料夾名稱可以命名為 `classes`  / ` model` 之類的，把上一集寫定義的 `class `搬進去
```ts
//src/classes/Invoice.ts

export class Invoice {

	client: string;
	
	details: string;
	
	amount: number;


	constructor(client: string, details: string, amount: number) {
	
		this.client = client;
		
		this.details = details;
		
		this.amount = amount;

	}


	format() {
	
		this.client = 'apple';
		
		return `${this.client} / ${this.details} / ${this.amount}`;
	
	}

}
```
在需要使用的頁面引入它
```ts
//app.ts
import { Invoice } from './classes/Invoice.js'; // 要注意，這裡是引入編譯後的js，不是ts


const invOne = new Invoice('nick', 'iphone', 500);

console.log(invOne);

invOne.client = 'aaa';

  

let invoices: Invoice[] = [];

  
invoices.push(invOne);

// console.log(invoices);

  

// invOne.client = 'mike';

console.log(invOne.client);

  

console.log('edit', invOne);
```

#### 結論
使用 module system 的優點是好維護、好擴充。儘管每多一個模組就需要發送一次額外的請求，這在網路速度慢或者請求量很大的時候可能會成為問題。然而，現代的 HTTP/2 協議可以讓多個請求在同一個連接上平行傳輸，因此不會像 HTTP/1.1 那樣受到「每次只能傳輸一個請求」的限制。

此外，打包工具如 Webpack 和 Rollup 不僅能將多個檔案「壓縮」成一個檔案，還可以進行許多其他的優化，例如刪除未使用的程式碼（也稱為樹搖（Tree Shaking））、最小化（Minification）和模組分割（Code Splitting）。這些優化可以使最終的檔案更小、載入更快。

只要你使用了 ES6 的模組語法，無論你的環境支援程度如何，你都可以透過各種工具將其轉換成你的目標環境可以接受的程式碼。例如，Babel 可以將 ES6 的 `import` 和 `export` 語法轉換成 CommonJS 的 `require` 和 `module.exports` 語法，這樣的程式碼就能在不支援 ES6 模組的 Node.js 環境下執行。Webpack 則可以將多個互相依賴的模組打包（bundle）成一個或者多個文件，並且自動處理模組之間的依賴關係。這讓我們能在瀏覽器環境下使用模組，而無需手動編寫 `<script>` 標籤或者配置模組加載器。

因此，即使 JS 和 TS 的 module system 在未經轉換的情況下可能無法在所有環境下工作，我們仍然可以利用轉譯工具和打包工具來使用這些強大的特性，並且享受到模組化、類型檢查和自動完成等優點，同時也不需要擔心程式碼在目標環境下的兼容性問題。

#### 補充資料
##### 什麼是HTTP/1.1 什麼是HTTP/2 ? HTTP/2是為了解決什麼問題？
**HTTP/1.1**：HTTP/1.1是HTTP協議的一個版本，於1997年正式發布。相較於前一個版本HTTP/1.0，HTTP/1.1 在效能和功能上做了許多改進和擴充，例如引入了持久連接（persistent connection，也稱為 keep-alive 或 connection reuse），允許在一個TCP連接上完成多個HTTP請求和回應，減少了因為連接和關閉TCP連接而造成的時間和資源消耗。此外，HTTP/1.1 還引入了對虛擬主機（virtual host）的支援，允許一台伺服器上運行多個網站。
**HTTP/2**：HTTP/2則是HTTP協議的最新主要版本，於2015年正式發布。它在HTTP/1.1的基礎上做了許多改進和優化，例如頭部壓縮（header compression）、伺服器推送（server push）、以及多路復用（multiplexing）。HTTP/2的設計目標是要提高網頁載入速度，並且降低網路延遲。
**HTTP/2解決的問題**：一個主要的問題是網頁的複雜度和資料量的增加，這使得在HTTP/1.1中，一個頁面可能需要發送大量的HTTP請求，而每個請求都會帶來一定的延遲。另一個問題是HTTP/1.1的"線頭阻塞"（Head-of-line blocking）問題，即在一個TCP連接上，如果前面的HTTP請求被阻塞了，那麼後面的請求也無法進行，即使後面的請求本身並沒有任何問題。HTTP/2通過多路復用來解決這個問題，允許在同一個連接上並行傳輸多個請求和回應。同時，HTTP/2還通過頭部壓縮和伺服器推送來進一步降低延遲和提高效能。
##### tsconfig 設定
除了`tsconfig.ts` 的備註說明外，也可以查看官方對於每個屬性的說明和範例：
[官方 Intro to the TSConfig Reference](https://typescript-v2-527-ortam.vercel.app/tsconfig)
