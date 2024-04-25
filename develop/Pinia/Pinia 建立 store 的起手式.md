---
date : 2022-05-1122:10
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [Pinia: The Enjoyable Vue Store](https://vueschool.io/lessons/define-your-first-pinia-store?friend=vuerouter) <br>
Author :: [[@VueSchool]] <br>
Topics :: [[Pinia MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
- 在src資料夾底下新建一個store資料夾
pinia可以將不同的資料類別用不同的js去做分類
假設目前有一個`userStore.js`的store
1. 引入pinia套件(固定語法)
`import { defineStore } from 'pinia'`
2. 起手式寫法
```
export const use+檔案名稱 = defineStore(檔案名稱,{
	//state
	
	//actions
	
	//getters	
})

```
3. 加入state(data),actions(computed),getters(method)
> defineStore('',{...})，第一個參數需用雙引號
```
import { defineStore } from 'pinia'

export const useUserStore = defineStore('userStore',{
	state: () => {
		return {
		
		
		}
	
	},
	actions: {
	
	
	},
	getters: {
	
	
	
	}

})

```