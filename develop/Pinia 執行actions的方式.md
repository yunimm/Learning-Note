---
date : 2022-05-1200:25
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [{Pinia: The Enjoyable Vue Store](https://vueschool.io/lessons/synchronous-and-asynchronous-actions-in-pinia) <br>
Author :: [[@VueSchool]] <br>
Topics :: [[-Pinia moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
在pinia中，會使用action(等同於function)載入資料
1. 假設從本地json引入檔案
```
//stores/userStore
import { defineStore } from 'pinia'

import users from '@/data/users.json' 

export const useUserStore = defineStore('userStore', {
	stats: () => {
		return {
			users: [],
		
		}
	
	},
	actions: {
		fill(){
			this.users = users
		
		}
		
	}
	
})

```

1.1 在需要引入資料的元件直接呼叫這個actions
```
//views/XXX.vue or components/XXX.vue

//要先載入store
//不需要使用pinia語法解構成響應資料
import { useUserStore } from '@/stores/userStore'

const user = useUserStore()

//運行actions

useUserStore.fill()

```