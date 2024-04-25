---
date : 2023-07-2621:05
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [Nuxt3 - 01 - 了解同構渲染 - SSR](https://youtu.be/0HrL_ardt38?t=2134)<br>
Author :: {作者名稱} <br>
Topics :: [[Nuxt3 MOC]]<br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# How to use

---

# Note
在nuxt3中其中一個渲染方式叫做universal-rendering(SSR + CSR)，在剛進站或是刷新畫面時會使用SSR，此時伺服器會回傳完整的html讓瀏覽器解析，所以seo可吃到關鍵字，搜尋引擎可以記住你的搜尋紀錄，後續的使用者交互行為就會是CSR，只向伺服器請求資料回來拼裝。原本我以為nuxt的SSR就是傳統SSR的方式，實際開發後才知道他是兩者的結合，甚至可以指定哪頁要使用SSR哪頁要用CSR([Hybrid Rendering](https://nuxt.com/docs/guide/concepts/rendering#hybrid-rendering))
![[Pasted image 20230726211052.png]]