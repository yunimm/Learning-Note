---
date : 2023-06-1122:20
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: {教學 URL} <br>
Topics :: [[-CS50 moc]] <br>
# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
1. Linear Search
2. Binary Search
3. Running Time
---

# Note
假設當前有七個置物箱，每個置物箱裡都有一張鈔票，我們要尋找存放鈔票面額為50的置物箱，該怎麼找？(每個置物箱的鈔票並沒有按照排序存放)
#### Linear Search
我們使用線性搜尋，依序查看每個置物箱
錯誤虛擬碼：
```
For each door from left to right 
	If 50 is behind door 
		Return true
	Else 
		Return false
```

為什麼錯？假設第一個箱子不是面額為50的鈔票，就會立即返回false，即使其他置物箱符合條件，也找不到。
正確虛擬碼：
```
For each door from left to right 
	If 50 is behind door 
		Return true
Return false

```

假設當前有七個置物箱，每個置物箱裡都有一張鈔票，我們要尋找存放鈔票面額為50的置物箱，該怎麼找？(每個置物箱的鈔票按照排序存放)
#### Binary Search
虛擬碼
```
If no door left 
	Return false 
//如果已經沒有剩下的箱子可以搜尋（也就是說，你已經檢查過所有的箱子），那麼返回false，表示沒有找到面額為50的鈔票
If 50 is behind middle door
	Return true
//如果中間的箱子裡的鈔票面額是50，那麼返回true，表示你找到了面額為50的鈔票。
Else if 50 < middle door
	Search left half
//如果中間的箱子裡的鈔票面額大於50（也就是說，你要找的50面額鈔票會在一個較小的面額中），那麼你就在左半邊的箱子中繼續搜尋。
Else if 50 > middle door
	Search right half
//如果中間的箱子裡的鈔票面額小於50（也就是說，你要找的50面額鈔票會在一個較大的面額中），那麼你就在右半邊的箱子中繼續搜尋。


//注意，這種二分搜尋法需要你的資料（在這裡是箱子裡的鈔票面額）已經預先按照順序排列。換句話說，左邊的箱子裡的鈔票面額必須小於右邊的箱子裡的鈔票面額。否則，這種搜尋方法就無法正確地工作。
```
更貼近程式語言的虛擬碼
```
if no doors left
	return false
if 50 is behind doors[middle]
	return true
else if (50 < doors[middle])
	search doors[0] thought doors[middle - 1]
else if (50 > doors[middle])
	search doors[middle + 1] thought doors[n - 1]


middle  = 陣列長度 / 2 四捨五入
```

#### Running Time
使用更貼近程式員或是計算機科學家的方式形容每個演算法之間的好與不好。
Big-O( Ο )計算時間由慢到快依序(上限，最糟的情況)：
- O(n²)
- O(n log n)
- O(n) - Linear Search
- O(log n) - Binary Search
- O(1)
Omega( Ω )計算時間由慢到快依序(下限，最好的情況)：
- Ω(n²)
- Ω(n log n)
- Ω(n) 
- Ω(log n)
- Ω(1) - Linear Search、 Binary Search
Θ(theta)，上下限的重合處
- Θ(n²)
- Θ(n log n)
- Θ(n) 
- Θ(log n)
- Θ(1)