---
date : 2022-09-0921:50
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️  +  💿  <br>
Source URL :: {教學 URL} <br>
Author :: [[@AC - ReactBeta]] [[@React思考模式]]<br>
Topics :: [[React MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
##### 如何使用
React中的輸入事件都是由原生的DOM API傳入的event去處理。
```js
	import React from 'react';

	function LoginForm() {
		return (
			<button
				onClick={(event)=>{console.log(event.target.value)}}
			</button>
		);
	}

	export default LoginForm;
```

---

# Note