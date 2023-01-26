---
date : 2022-05-0705:06
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [avaScript基本功修練：Day29 - axios基本語法與練習(GET、POST請求)](https://ithelp.ithome.com.tw/articles/10253259) <br>
Author :: [[@IT邦]] <br>
Topics :: [[-Fetch API MOC]], [[-Axios MOC]] <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
axios 回傳的物件是Promise(fulfilled)狀態，所以要用`.then` `.catch`承接請求成功或是失敗的狀態。

一般來說可以這麼寫
```
axios.get('URL')
.then(function(response){
	console.log(response.data)
})
.catch(function(error){
	console.log(error.message)
})
````
使用ES6 arrow function 
```
axios.get('URL')
.then((res) => console.log(res.data))
.catch((err) => console.log(err.message))
```

---

介接api時，需要帶入`params`，可以直接將`params`寫入URL
```
..api/?gender=female&nat=us
```

也可以使用這樣的寫法帶入 :
```
axios.get('URL',{
	params:{
		gender: 'female',
		nat: 'us'
	}
})
.then((res) => console.log(res.data))
.catch((err) => console.log(err.message))
```

改寫成非同步語法 :
```
async function fetchDate() {
	try {
		const res = await axios.get('URL',{
			params: { key: 'value' }
			
			console.log(res.data)
		})
		
	} catch(error) {
		console.log(error.message)	
	}
}
```

---

同時發出多個請求，使用`Promise.all`語法帶入多個請求api的function : 
```
Promise.all([fetchData(),getUser()]) {
	.then((res) {
		const data = res.[0]
		const user = red.[1]
	})
}
```

---
