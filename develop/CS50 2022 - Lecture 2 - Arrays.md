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
1. compiling
2. debugging
3. 型別
4. 不要寫magic number
5. command line argument
6. cowsay
7. exit status
8. cryptograph
---

# Note
## compiling
##### 反向編譯

## debugging
#### 如何使用vscode debug


## 型別
##### 每種型別佔據記憶體的byte都不同：



- string ? 
  `string`的`byte`是動態的，會依照字數不同而做變化，C會將`string`當作陣列儲存在記憶體中，`string`和`array`的差別在於，`string`在最後一個字尾後會加上`\0`, 表示這段記憶體位置是儲存`string`

## command line argument
前兩週都是用問的寫法`get_string` `get_int`... 
透過詢問的方式取得要印出的參數
```
#include<stdio.h>

int main(void)
{
	int n = get_int("Number: ");
	printf("%i\n", n);
}
```
在這週我們學到一個新的方法，在function內帶入要使用的參數，在執行command line時一併輸入function的參數
``` greet.c
#include <stdio.h>
int main(int argc, string argv[])

{

printf("hi,%s\n",argv[1]);

}
	-------執行command line------
make greet
./greet Apple
印出
hi, Apple

```


## cowsay
透過 ASCII 產生一個角色 (預設為母牛)，並說出一段話
![[截圖 2023-05-28 下午10.27.22.png]]

## exit status
C語言預設`return 0` 執行`echo $` 就可以得到現在return的值

## cryptograph 密碼學

### encryption 加密

### decryption 解密




[CS50 Manual](https://manual.cs50.io/)

`