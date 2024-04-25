---
date : 2022-10-2622:27
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [# React Hook Form V7 - Get Started](https://www.youtube.com/watch?v=DN8v7_RbVlc)<br>
Author :: {頻道名稱} <br>
Topics :: [[React MOC]] [[React Library]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: React Hook Form 基礎教學，綁定、驗證、印出
- 這套套件特別的點是他支援鍵盤操作（作者在影片8:15特別提的）
---

# Summary 

register，將input和Hooks進行綁定
使用方式：
	將原本<input /> 的name替換成{...register('名字')}，這樣就完成綁定了。
	
watch，即時印出輸入內容
使用方式：
	console.log(watch())
handleSubmit，一個cb function，搭配onSubmit在表單送出時執行，會印出表單上的值
```js
<form onSubmit={handleSubmit((data)=>{console.log(data);})}>
</form>
```
formState:{errors}，錯誤捕捉，當有出錯時可以印出結果或是當作判斷條件
```js
console.log(errors.firstName)
errors.firstName&&

或是把錯誤訊息塞在require裡面也行
<input {...register("name"),{require:'this is require',maxLength:4}}/>
console.log(errors.name.message);

甚至每個驗證都能有自己的錯誤提示，如附圖
<input {...register("name"),{require:'this is require',maxLength:{value:4, message:'You excced max length'}}}/>
console.log('errors', errors);
```
---
![[截圖 2022-10-26 下午11.03.22.png]]
# Note
1. 作者建議使用TS，因為使用TS時，你會先定義型別，在綁定時如果打錯名字，VSCODE就會先幫你噴錯，不用等到瀏覽器噴錯
範例code```
```ts
type FormValues = {
name: string;
lastName: string;
age: number;
}

export default App () => {
	const {register} = useForm<FormValues>();
	return (
		
		<input {...register("name1")}/>
		//此時vscode就會噴錯給你看，name1
	)
	
}
```

2. 關於驗證的兩種方式： 
	- building，使用html原生方式，當驗證失敗時沒辦法進入下一個輸入框
	```js
	<input {...register("name"),{require:true,maxLength:4}}/>
	<input {...register("number"),{valueAsNumber:true}}/>
	
	```
	==valueAsNumber== input type是number的狀況下，輸出結果一樣式字串，但是加了這段就可以轉成數字了！
	- schema