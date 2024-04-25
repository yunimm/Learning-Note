---
date : 2023-01-2623:19
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️ <br>
Source URL :: [[js面試力]] <br>
Author ::  [[＠卡斯伯]] <br>
Topics :: [[JavaScript MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 陳述式與表達式最大差異在於會不會回傳值，陳述式不會，表達式會

---

# Summary 
表達式判斷法：
- 純值
- 變數
- 運算子 
```
a = 1 //回傳1
delete a //回傳true
typeof 'abc' //回傳String
```
- 執行函式
- 正規表達式
- 函式表達式

陳述式判斷法：
- 宣告(var, const, let) 
```
var a = 1; //雖然有包含表達式，但並不會回傳值，所以還是屬於陳述式
```
- 流程控制(block, if...else)
- 迴圈(for, for...in)
- 其他(import, export)
---

# Note
