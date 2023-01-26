---
date : 2022-05-0706:25
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
因應每次要介接api時都需要重複帶入一樣的參數(URL,headers,params,data,method..)，axios提供了`config`的寫法 : 

```
axios({
	method:'get',
	url:'URL',
})
.then(res => console.log(res.data))
.catch(err => console.log(err.message))

axios({
	method:'post',
	url:'URL',
	data: {
		account:'root@mail.com',
		password:'12345678'
	},
	params: {
		id: 123
	}
})
.then(res => console.log(res.data))
.catch(err => console.log(err.message))


```

axios提供了`.create` 預設`config`內容

```
const instance = axios.create({
	baseURL: '',
	timeout: 1000,
	headers: {'X-Header': 'foo123'}
})
```