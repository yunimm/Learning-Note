---
date : 2022-05-2420:41
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL ::[Day_14 : 讓 Vite 來開啟你的Vue 之 Composition API](https://ithelp.ithome.com.tw/articles/10272703) <br>
Author :: [[@IT邦]]<br>
Topics :: [[-Composition API]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 了解CompositionAPI解決了什麼問題

---

# Summary 

---

# Note
1. 解決 [[未寫 Vue2 OptionAPI]]缺點。OptionAPI優點是讓初學者好上手，強制規定資料、方法、生命週期要寫在哪裡。缺點可讀性問題，商業、功能邏輯會散落在四處，隨著專案規模變大會更難維護。
2. 邏輯複用問題，在Vue2要使用[[Vue2 Mixins]]才行。
3. 對TS的支持度差，[[未寫 Vue3響應式數據底層原理]]重新使用TypeScript改寫

**什麼是Composition API?**

setup語法:
將原本Option API的分散式的撰寫架構改成同樣邏輯聚在一起的寫法就屬於CompositionAPI

export語法:
取代mixin的新作法也是CompositionAPI特色，將撰寫在js裡的商業邏輯export至.vue檔案重複使用，減少重複的程式碼。

```js
//Counter.js 
//需要重複使用的功能

import { ref } from 'vue';
export default function() {
  const count = ref(0);
  const double = computed(() => count.value * 2) 
  const increment = () =>count.value ++ } 
	
  return { 
    count,
    double,
    add 
	};
  }

```

```js
// Component1 
<script> 
import Counter from './Counter.js';
==import { ref, computed } from "vue";==
export default { 
  setup() {
  
    const {
	  count,
	  double,
	  add 
	} = Counter();
	return {//這裡回傳給 <template> 使用的 資料 
	  count,
	  add,
	  double 
	} 
  } 
} 
</script>
```