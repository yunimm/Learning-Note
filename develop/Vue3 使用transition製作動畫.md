---
date : 2022-05-1510:20
aliases : []
---
# Metadata
Status :: #ð± <br>
Note Type :: #ð¨/ð¿ <br>
Source URL :: [Vue 3 Animations Tutorial #3 - Transition Component](https://www.youtube.com/watch?v=NzFRZKho23k&list=PL4cUxeGkcC9ghm7-iTfS9n468Kp7l9Ipu&index=3) <br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[Animation moc]] <br>
Cover ::

# Evergreen Note

Question :: éç¯æç« ä¸»è¦å¨èªªä»éº¼ ?

Answer ::

---

# Summary 

---

# Note
å¨æ³è£½ä½åç«ææçåä»¶åä¸`<transtiton></transition>`tagï¼è£¡é¢ççµä»¶å°±è½å¤ åå°åç«èªæ³ï¼çµ¦`<transition>` å ä¸åå­å°±è½å¤ é¸ååç«ç¸écssé¸æå¨
```vue
<transition name="fade">
	<h1>ä½ å¥½å</h1>
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
åç«é¸æå¨:
```
from: åå§å¼
to: çµæå¼
active: éæ¸¡

é²å¥é é¢æ:
.enter-from 
.enter-to
.enter-active

é¢éé é¢æ:
.leave-from
.leave-to
.leave-active

```
	
