---
date : 2023-02-2022:30
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: 
[前後端分離與 SPA](https://blog.techbridge.cc/2017/09/16/frontend-backend-mvc/)
[關於mvc的定義](https://blog.turn.tw/?p=1539)
[MVC與Model 2的變異與結合](https://www.ithome.com.tw/voice/77330)
[MVC Explained in 4 Minutes](https://www.youtube.com/watch?v=DUg2SWWK18I)
Author :: {作者名稱} <br>
Topics :: [[軟體架構MOC]] <br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 

- 你認為的MVC不是MVC，現在討論的MVC其實是Model2，Model2和MVC最大的差異為view對model沒有觀察者模式 ? (不確定) 
- MVC有分為前端或後端MVC，並沒有絕對的實踐方式，但重點在於職責分離的概念。
- Controller(控制器) ：接收瀏覽器請求指示Model, View提供對應的資料，將需要的資料組成HTML後回傳給瀏覽器進行解析。
- Mode(資料)：依照Controller指示從資料庫撈出對應的資料並整理資料後回傳給Controller。
- View(視圖) : RenderHTML。
---

# Note
MVC架構範例：
![[MVC_Explained_In_4minutes_Img01.png]]![[MVC_Explained_In_4minutes_Img02.png]]![[前後端分離與SPA_Img01.png]]