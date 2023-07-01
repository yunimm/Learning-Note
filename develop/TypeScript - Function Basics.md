---
date : 2023-06-2723:26
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript - Function Basics](https://youtu.be/jXoSaX_yFh4)<br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 關於function的基本型別定義用法

---

# Summary 

---

# Note
function的型別定義和其他型別寫法不同，是大寫開頭`Function` 
```ts
let handler:Function;
```

也可以順便定義arguments和回傳值
```ts
let handler: (a: number, b: number | string) => void;
```

可以對function的arguments定義型別
```ts
handler = (a:number,b:number) => {
	console.log(a + b);
};
```

有時候arguments可能不是只有一種型別，這時可以使用聯集加上其他型別
```ts
handler = (a:number,b:number | string) => {
	console.log(a + b);
};
```

也有時候不會用到該argument，此時可以搭配條件運算符寫法，如果條件為真才帶入型別定義
```ts
handler = (a:number,b:number | string, c?:string) => {
	console.log(a + b);
	console.log(c);
};

handler(10,5,'11')//印出15,印出'11'
```

給預設值的寫法也可以，這時候就不需要條件運算符了
```ts
handler = (a:number,b:number | string, c:string = '10') => {
	console.log(a + b);
	console.log(c);
};

handler(10,5); //印出15,印出'10'
```

通常 IDE 會自行推斷回傳的型別，不用特別定義回傳值的型別，但如果今天是個很大的function，建議還是標註回傳型別，如果沒有要回傳值就定義`void`，其他就依照回傳型別定義
```ts
handler = (a:number, b:number | string, c:string = '10'): number => {
	return a + Number(b);
};

handler = (a:number,b:number | string, c:string = '10'): void => {
	console.log(a + Number(b));
	console.log(c);
};
```