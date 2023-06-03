---
date : 2023-06-0314:53
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [TypeScript - Compiling TypeScript](https://www.youtube.com/watch?v=iTZ1-85I77c&list=PL4cUxeGkcC9gUgr39Q_yD6v-bSyMwKPUI&index=2)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]] <br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 透過小專案了解TS如何編譯

---

# Summary 
### 當你完成 TypeScript 程式碼編寫，可以使用 `tsc 檔案名.ts -w` 指令自動將其轉換為 JavaScript，並在檔案有所變動時重新編譯。

---

# Note
編寫完TS檔案後，需在terminal執行指令`ts 檔案名.ts`，資料夾內就會多了編譯完的JS檔案，但如果每次改完TS檔案都要重複執行這個指令有點太麻煩了，所以可以這麼寫`ts 檔案名.ts -w` ，加上 `-w` 參數後，這個指令將進入 "watch" 模式。在此模式下，只要 TS 檔案有任何變動，終端機就會自動重新進行編譯。這個功能可以省去手動編譯的步驟，使得開發流程更加順暢。