---
date : 2022-05-2423:01
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [vue3新语法糖——setup script](https://juejin.cn/post/6944190150406570020) <br>
Author :: [[@掘金]] <br>
Topics :: [[-Composition API]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
為什麼要使用`<setup script>`語法糖 ?

如果不使用語法糖，import元件、component 資料、component function，都需要retrn(手動註冊)後才能使用
```
<script>
	export default {
	  setup() {
		const state = reactive({ count: 0 })
	  }
		return {
		  state
		}
	}
</script>
```

```
<script setup>
	//直接寫
</script setup>
```