---
date : 2023-07-0115:45
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #10 - Function Signatures](https://youtu.be/TZNbzyY6hMU) <br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-TypeScript MOC]]  

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
記錄了影片中的使用方法，但看完後我覺得應該有更好的寫法才對，影片中的寫法等於是事先定義了型別然後真的使用function時再定義一次，如果和事先宣告的型別不同的話則編輯器會出現錯誤提示，但我覺得應該沒有必要寫兩次....?這部分的做法要再觀察看看....
```ts
let greet:(a:string, b:string) => void;

greet = (name:string, greeting:string)=>{

console.log(`${name} and ${greeting}`);

}

  
let calc:(a:number,b:number,c:string)=>number;

calc = (numOne:number, numTwo:number, action:string) => {

if(action === 'add') {

return numOne + numTwo;

} else { //這邊要注意，如果沒有定義else會噴錯，因為我們漏判斷了else狀況會回傳什麼

return 0;

}

}

let logDetails: (obj: { name: string, age: number }) => void;

type person = { name: string, age: number };

logDetails = (ninja: person) => {
  console.log(`${ninja.name},${ninja.age}`);
};


```

留言區其他寫法：
```ts
type Calc = (a: number, b: number, c: string) => number;


let calcFunction: Calc = (a, b, c) =>{

console.log(c);

return a + b;

}
```