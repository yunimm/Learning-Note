---
date : 2022-05-1201:57
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [{Pinia: The Enjoyable Vue Store](https://vueschool.io/lessons/synchronous-and-asynchronous-actions-in-pinia) <br>
Author :: [[@VueSchool]] <br>
Topics :: [[Pinia MOC]],[[-Async moc]],<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
使用async await語法引入資料
```
//stores/userStore
import { defineStore } from 'pinia'

export const useUserStore = defineStore('userStore', {
	stats: () => {
		return {
			users: [],
			products: [],
		}
	
	},
	actions: {
		asyun fill(){
			this.users = (await import('@/data/users.json')).default
			this.products = (await axios.get('...')).data
		}
		
	}
	
})

```

在需要引入資料的元件直接呼叫這個actions
```
//views/XXX.vue or components/XXX.vue

//要先載入store
//不需要使用pinia語法解構成響應資料
import { useUserStore } from '@/stores/userStore'

const user = useUserStore()

//運行actions

useUserStore.fill()

```