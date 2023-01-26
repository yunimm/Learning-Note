---
date : 2022-05-1510:20
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [Vue 3 Animations Tutorial #3 - Transition Component](https://www.youtube.com/watch?v=NzFRZKho23k&list=PL4cUxeGkcC9ghm7-iTfS9n468Kp7l9Ipu&index=3) <br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[Animation moc]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
在想製作動畫效果的元件包上`<transtiton></transition>`tag，裡面的組件就能夠吃到動畫語法，給`<transition>` 加上名字就能夠選取動畫相關css選擇器
```vue
<transition name="fade">
	<h1>你好啊</h1>
</transition>

<style>
	fade-enter-from {
		color: blue;
	}
	fade-enter-to {
		color: red;
	}
	fade-enter-active {
		transition-duration: 2s;

	}
</style>
```
動畫選擇器:
```
from: 初始值
to: 結束值
active: 過渡

進入頁面時:
.enter-from 
.enter-to
.enter-active

離開頁面時:
.leave-from
.leave-to
.leave-active

```
	
