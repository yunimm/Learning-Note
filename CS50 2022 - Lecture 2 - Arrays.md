---
date : 2023-05-2814:28
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [{CS50 2022 - Lecture 2 - Arrays} ](https://www.youtube.com/watch?v=XmYnsO7iSI8&t=1815s)<br>
Topics :: [[-CS50 moc]]<br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
1. Arrays
2. c語言中的型別
4. 不要寫magic number
---

# Note
### 型別
每種型別佔據記憶體的byte都不同：



- string ? 
  `string`的`byte`是動態的，會依照字數不同而做變化，C會將`string`當作陣列儲存在記憶體中，`string`和`array`的差別在於，`string`在最後一個字尾後會加上`\0`, 表示這段記憶體位置是儲存`string`

### command line argument

```
#include <stdio.h>

int main(argc, argv[])
{
	
}
```

[CS50 Manual](https://manual.cs50.io/)
