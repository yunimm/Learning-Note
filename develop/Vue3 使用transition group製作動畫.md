---
date : 2022-05-1511:39
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [Vue 3 Animations Tutorial #6 - Group Transitions](https://www.youtube.com/watch?v=gbCxH5KCeBg&list=PL4cUxeGkcC9ghm7-iTfS9n468Kp7l9Ipu&index=6) <br>
Author :: [[@The Net Ninja]]<br>
Topics :: [[-Vue3 moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
延續[[Vue3 使用transition製作動畫]]
`<transition-grop>`可以運用在多個element,例如
```vue
<ul>
	<li v-for="item in items" :key="item.id">
	</li>
</ul>

//將ul替換transition-grop,tag="被替換掉的tag名字",name="這組tag名"
<transition-grop tag="ul" name:"items">
	<li v-for="item in items" :key="item.id">
	</li>
</transition-grop>
```