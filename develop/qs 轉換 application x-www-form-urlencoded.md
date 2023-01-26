---
date : 2022-05-0806:50
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [TDX api 串接將 ajax 改為 axios，解決 415 錯誤，解決 headers content-type 無法更新 ](https://ithelp.ithome.com.tw/articles/10258164)<br>
Author :: [[@IT邦]] <br>
Topics :: [[-Fetch API MOC]], [[-Axios MOC]] [[-Vue3 moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 將`application/json`格式轉成`application/x-www-form-urlencoded`

---

# Summary 

---

# Note
安裝qs外掛，使用[官方提供的es6語法](https://github.com/axios/axios#example)
```import qs from 'qs';
const data = { 'bar': 123 };
const options = {
  method: 'POST',
  headers: { 'content-type': 'application/x-www-form-urlencoded' },
  data: qs.stringify(data),
  url,
};
axios(options);
```

實際應用在TDX專案:

![[截圖 2022-05-08 上午7.13.25.png]]
```
function handleSubmit() {

const parameter = {

grant_type: 'client_credentials',

client_id: 'yuu9916-227e67ac-b78a-41bb',

client_secret: 'd6552544-b840-4ba7-8b51-0ee7cb500e0a',

}

const tokenURL =

'https://tdx.transportdata.tw/auth/realms/TDXConnect/protocol/openid-connect/token'

axios({

method: 'post',

url: tokenURL,

data: qs.stringify(parameter),

headers: { 'content-type': 'application/x-www-form-urlencoded' },

})

.then((res) => console.log(res.data))

.catch((err) => console.log(err.message))

}

```

- 將需要帶入的資訊(type, id , secret) 賦值給`parameter`

- 使用`axios config` 寫法帶入`method`(請求方式),	`url`(請求網址),`data`(post方式需要帶入data)

- 我們在`data` 裡進行編碼的程序
---
# Situation
介接TDX API時發生415錯誤，經多方餵狗發現是axios發出請求時帶入的格式為`json` TDX 則是發送`x-www-form-urlencoded`

