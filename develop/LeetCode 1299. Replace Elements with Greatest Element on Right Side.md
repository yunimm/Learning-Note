---
date : 2023-01-2515:13
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨🧠 <br>
Topics :: [[Leetcode MOC]]<br>
# Evergreen Note

Question :: LeetCode 1299. Replace Elements with Greatest Element on Right Side

Answer :: 

---

# Preliminary solution
題目重點為，當前index往右最大的值（不包含當前index指向的值）
```javascript
Input:  arr = [17,18,5,4,6,1]
Output: [18,6,6,6,1,-1]

arr.length -1 = -1 //必定條件，索引值最後為-1
迴圈只需要arr.length - 2 ~ 0這個段落

從陣列尾開始遍歷，
當索引值為arr.length-2，指針指向6，6的右邊是1，當前最大值為1
當索引值為arr.length-3，指針指向4，4的右邊是6,1，當前最大值為6
當索引值為arr.length-4，指針指向5，5的右邊是4,6,1，當前最大值為6
當索引值為arr.length-5，指針指向18，5的右邊是5,4,6,1，當前最大值為6
當索引值為arr.length-6，指針指向17，5的右邊是18,5,4,6,1，當前最大值為18


let max = -1;
arr[arr.length-1] = -1
for(let i = arr.length -2; i <= 0; i--) {
	if(arr[i+1] > max) {
		max = arr[i+1];
		arr[i] = max;
	} else {
		arr[i] = max;
	}
}

結果：
##### Your input

[17,18,5,4,6,1]

##### Your answer

[17,18,5,4,6,-1]  

##### Expected answer

[18,6,6,6,1,-1]

```



---

# Note

初次解法的盲點：
1. 不需要再列舉當前指針右邊的值，只要和最大值做比較就可以了
``` javascript
當前最大值max為arr[arr.length-1] = 1
從陣列尾開始遍歷，
if max值 > arr[i] => max不變，arr[i] = max;
else max值 < arr[i] => max變成arr[i]，arr[i] = 原本的max，因此需要多宣告一個變數存原本的max值 => temp = max, max = arr[i], arr[i] = temp;

當索引值為arr.length-2，指針指向6， 6 > max(1) => else，arr[i] = 1
當索引值為arr.length-3，指針指向4， 4 < max(6) => if, arr[i] = 6
當索引值為arr.length-4，指針指向5， 5 < max(6) => if, arr[i] = 6
當索引值為arr.length-5，指針指向18， 18 > max(6) => else，arr[i] = 6
當索引值為arr.length-6，指針指向17， 17 < max(18) => if, arr[i] = 18

```