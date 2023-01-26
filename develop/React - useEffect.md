---
date : 2022-08-2800:15
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: {教學 URL} <br>
Author :: [[@AC - ReactBeta]] [[@React思考模式]]<br>
Topics :: [[-React Moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
##### 如何使用
```js
useEffect(()=>{
	/*建立、更新元件的副作用區*/
	return ()=>{
		/*移除元件的副作用區*/
	}
},[])/*用來限制副作用要以哪些state和props作為觸發條件的arra*/
```
##### 生命週期
- 初始化（第一次渲染時）：
1. 建立、呼叫function componet
2. 建立Virtual DOM、更新DOM
3. 渲染畫面
4. **呼叫useEffect副作用**
- 更新（偵測到state、props被改變時）：
1. 重新呼叫function componet
2. 在Virtual DOM比較所有和原始DOM不一樣的地方
3. 真正更新DOM
4. 渲染畫面
5. **透過檢查useEffect中的array，判斷該useEffect是否「和被改變的」state/props」有關係，有則呼叫該useEffect的副作用**
6. 如果有修改state、props，則再重複一次上述「更新」的生命週期
#####移除
1. 移除元件
2. **呼叫useEffect第一個參數回傳的清除函式**

![[04.png]]
---

# Note
使用useEffect提醒：
> 避免在第一個參數的副作用定義區，使用『沒有被加入至第二個相依參數array的state/props』，進而導致產生非預期的錯誤。
> 
```js
/*--------bad---------*/
useEffect(()=>{
	console.log(text)
},[])
/*------correct-------*/
useEffect(()=>{
	console.log(text)
},[text])
```
使用useEffect時機：
- 向後端呼叫API(待補useEffect、Suspense呼叫API差異）
- 使用外部函式庫
- 註冊/清除監聽器
-   useEffect 是個多功能函數，實務上常用的操作：
    1.  使用useEffect仿造Component出生(mounted)和死亡(unmounted)
        -   Compoment的出生或死亡會照綁定的變數更改而改變
        ```js
        useEffect(()=> {
        	/*mounted*/
			console.log('%cmounted', 'background:#2ecc71');
		    return () => {
			/*unmounted*/
		      console.log('%cunmount', 'background:#e67e22');
		    };
		},[])
		/*函數後面的參數為“相依性”*/
		/*加上空陣列代表什麼都不關注，只專注在元件的出生和死亡*/
		```
	2. 使用useEffect變更資料
		- mounted時會跑一次代碼
		```js
		useEffect(()=> { 
			/*mounted*/ 
			console.log('%cmounted', 'background:#2ecc71'); 
			return () => { 
			/*unmounted*/ 
			console.log('%cunmount', 'background:#e67e22');
			};
		},) 
		/*相依性的欄位什麼都沒寫代表什麼都關注(浪費效能)*/
		/*只要componet更新，一定會被執行*/
		
		```

