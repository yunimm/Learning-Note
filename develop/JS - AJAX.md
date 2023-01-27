---
date : 2023-01-2719:03
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️ <br>
Source URL :: [[js面試力]] [[B站教學]] [教學連結](https://www.bilibili.com/video/BV1cR4y1P7B1/?spm_id_from=333.999.0.0)<br><br>
Topics :: [[-Javascript moc]]<br>

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
AJAX : 非同步的Javascript和XML的瀏覽器與伺服器溝通的方法。瀏覽器能以非同步的方式對伺服器發出請求並取得資料且瀏覽器不需要重新整理就可以將資料渲染至畫面上，達到更好的使用者體驗

---

# Note
傳統網頁請求方式：
	1. 輸入URL
	2. 點擊超連結
	3. 送出表單
	4. 使用Javascript送出請求
	   `window.open(url)`
	   `document.location.href = url`
	   `window.location.href = url`

缺點：
- 伺服器處理使用者每個行為都需要重新載入頁面(即便只是部分資料更新，也是需要重新向伺服器請求全部資料)瀏覽器收到資料後再全部重新渲染。如果遇到資料量太龐大，則瀏覽器畫面則會卡住，造成使用者體驗不佳。

圖解：
![[Pasted image 20230127195751.png]]
[圖片來源](https://bsscommerce.com/blog/javascript-jquery-ajax-are-they-the-same-or-different/)