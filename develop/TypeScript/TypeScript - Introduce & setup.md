---
date : 2023-06-0314:03
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [TypeScript - Introduce & setup](https://www.youtube.com/watch?v=2pZmKW9-I_k&list=PL4cUxeGkcC9gUgr39Q_yD6v-bSyMwKPUI&index=1) <br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[TypeScript MOC]] <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 介紹TS用途和安裝環境

---

# Summary 
TypeScript (TS) 是一種強大的開發工具，提供了靜態型別檢查、現代 JavaScript(JS) 特性支援以及額外的功能（如泛型、接口和元組），以優化和加速我們的開發流程。然而，即使 TS 在我們的開發工作中扮演著重要的角色，實際上瀏覽器和大多數 JS 環境只能理解和解釋 JS 程式碼。
TS 提供了一個稱為 "tsc" 的命令行工具來完成這個編譯過程。這個工具可以將TS程式碼轉換成純 JS，並且可以配置來適應不同的目標環境和模塊系統。這樣一來，我們就可以在開發過程中利用 TS 提供的所有優點，而不需要擔心終端用戶的瀏覽器是否支援 TS。

---

# Note

#### Alternative to Javascript(superset) 
JS的超集，有JS所有功能並添加了一些新的功能，例如強型別、靜態類型檢查。
#### Allow us to use strict type 
可以使用嚴格的型別。在宣告變數或是function參數時需要指定型別，並且會在編譯時檢查型別是否正確，有助於在程式碼執行前就發現並防止錯誤，進而提高程式碼的可讀性和可維護性。
#### Supports modern features (arrow functions, let, const) 
支援es6以後的語法，例如箭頭函式、let、const
#### Extra features(generics, interfaces, tuples etc) 有更多的型別判定
除了原有的JS語法特性外，TS添加了一些新的特性，例如：泛型(generics)、接口(interfaces)、元組(tuples)等

TS幫助我們開發，但事實上瀏覽器還是只認得JS，所以在開發過程中我們需要將TS編譯成瀏覽器看得懂的JS檔案