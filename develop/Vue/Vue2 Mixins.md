---
date : 2022-05-2611:06
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: [官方Minin說明](https://v3.cn.vuejs.org/guide/mixins.html#%E5%85%A8%E5%B1%80-mixin) <br>
Author :: [[@Vue官方文件]]<br>
Topics :: [[Vue2 MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: mixin的使用與缺點

---

# How to use
參考官方教學影片[]()
設置mixin檔案
```js
//exampleMixins.js
export const exampleMixin = {
	creatde() {
	  console.log('Hello from the mixin')
	}
}

```
```js
//example.vue
<script>
import { exampleMixin } from '../mixins/exampleMixin.js'
export default {
	mixins: [exampleMixin]
}
<script>
```

---
# Tips
- Order of operations: mixin runs before conponent  / Mixins的執行順序優先於組件
```js
//exampleMixins.js
export const exampleMixin = {
	creatde() {
	  console.log('Hello from the mixin')
	}
}

```
```js
//example.vue
<script>
import { exampleMixin } from '../mixins/exampleMixin.js'
export default {
	mixins: [exampleMixin],
	created() {
	  console.log('Hey from the component')
	}
}
<script>
```
輸出結果：
```js
'Hello from the mixin'
'Hey from the component'
```
- If you hava conflicting data, the component's wins out. 如果有同樣的資料同時存於Mixins和component,component優先順序大於Mixins
```js
//exampleMixins.js
export const exampleMixin = {
	data() {
	  return {
	  	message: 'Hi!It's a good day!'
	  }
	}
}
```
```js
//example.vue
<script>
import { exampleMixin } from '../mixins/exampleMixin.js'
export default {
	mixins: [exampleMixin],
	data() {
	  return {
	    message: 'I don't like it'
	  }
	},
	created() {
	  console.log(this.message)
	}
}
<script>
```
輸出結果：
```js
'I don't like it'
```
- 
- 

---

# Note
可以重複使用的資料和方法，只要是OptionAPI裡的選項，都能夠抽出來做成Mixins。
引入mixin時，所有的資料都會和原本的組件混合。
缺點:
- mixin名字可能會和組件裡的名字重複，因為在導入minin時，所有的資料都會被合併至組件中。
- 不能傳遞參數來改變minin裡的商業邏輯