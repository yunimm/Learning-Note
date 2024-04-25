---
date : 2023-07-0115:19
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [TypeScript Tutorial #9 Type Aliases](https://youtu.be/AmpwfbdFYL8) 
<br>Author :: [[@The Net Ninja]]<br>
Topics :: [[TypeScript MOC]]  <br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
當我們在定義function arguments型別時，可能會有好幾個function arguments都是相似的型別定義，此時我們可以將它抽出共用變數。
抽出前：
```ts
const logDetails = (uid:string | number, item:string) => {

console.log(uid,item);

}

const greet = (user:{name:string,uid:string | number}) => {

console.log(user);

}
```
抽出後：
```ts
type stringOrNum = string | number;
type userObject = { name: string, uid: stringOrNum };


const logDetails = (uid:stringOrNum, item:string) => {

console.log(uid,item);

}

const greet = (user:userObject) => {

console.log(user);

}


```