---
date : 2022-09-0922:55
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️  +  💿  <br>
Source URL :: {教學 URL} <br>
Author :: [[@AC - ReactBeta]] [[@React思考模式]]<br>
Topics :: [[-React Moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: `<input>`,`<textarea>` 的用法，兩者用法一樣

---

# Summary 
##### 如何使用
- 取得`<input>` 輸入值是用`onChange`不是用`onClick`
- 使用`onChange`觸發修改事件並使用`setState`改變`state` 
```jsx
	<input type="text" 
		onChange={(event)=>{/* 用event.target.value去setState */}}> 
    </input>
```
- 使用`useState` 紀錄輸入的值和改變的方法
```jsx
	const [account, setAccount] = useState('');
```
- 將`state`綁定在`value`
```jsx
	<input type="text" value={account}></input>
```



---

# Note
###### defaluValue 與 value差異
在jsx中：
初始值為`defaultValue` ：只有在建立元件時被觸發
目前input輸入的值為`value`：input值始終跟著state，state的值也隨著input值改變而更動（控制/受控組件 controlled component ）

實作範例：
以下範例中，因為我們已經在初始值設定在state，所以defaultValue存在沒有意義
```jsx
import React, { useState } from 'react';

  
/* input/text與onChange */

function LoginForm() {

	const [account, setAccount] = useState('快來輸入我');
	
	//const defaultText = '快來輸入我'
	
	return (
	
	<div>
		<input
		//關閉input
		disabled={true}
		type="text"
		// defaultValue={defaultText}
		value={account}
		onChange={(event) => {setAccount(event.target.value);}}>
		</input>
	
		<div>目前account:{account}</div>
		
		//清空value
		<button
		onClick={() => {
		setAccount('');
		}}>	
		</button>
		
	</div>
	
	);
}

export default LoginForm;

```
