---
date : 2022-05-1123:45
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [Pinia: The Enjoyable Vue Store](https://vueschool.io/lessons/access-state-from-a-pinia-store) <br>
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
在store定義好state後，在需要使用store的view/components載入states
1. 方法1，使用storeToRefs語法載入
```
import { useUserStore } from '@/stores/userStore'
import { storeToRefs } from 'pinia'

const { users } = storeToRefs(useUserStore())
```

2. 方法2，使用變數方式載入
```
const users = userUserStore()
```

3. 方法3，
>使用傳統解構寫法也可以引入資料，不過資料就不是響應式資料

```
const userStore = useUserStore()
const { users } = userStore 
```