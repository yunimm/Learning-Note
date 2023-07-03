---
date : 2023-07-0320:06
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #14 - Modules](https://youtu.be/EpOPR03z4Vw)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
隨著專案規模增長，可能會需要將程式碼進行模組化，例如拆成 DOM 交互行為、Fetch API、Auth等等，不同檔案，方便後續好擴充和維護。在 JS ES6 時新增了 module system 的支援，同樣的 TS 也同樣支援這個特性，並且加入了一些額外的功能，例如類型檢查和自動完成。要注意的是，JS 和 TS 的 module system（ES6 的 `import` 和 `export` 語法）本身並不被所有的瀏覽器支援，尤其是舊版的瀏覽器。然而，我們可以使用如 Webpack 和 Babel 這樣的工具，將使用了這些新特性的程式碼轉換（或稱為「轉譯」、「編譯」）成舊版瀏覽器可以理解和執行的程式碼。這種轉換過程常常被稱為「下轉譯」（Down-Transpiling）或「轉譯」（Transpiling）。
##### 如果今天沒有使用打包工具，我們該如何設定 tsconfig ? 
- "module": "commonjs", 改成 "es2015"