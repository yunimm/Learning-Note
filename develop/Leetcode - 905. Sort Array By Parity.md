---
date : 2023-01-2009:19
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨🧠 <br><br>
Topics ::[[ -Leetcode MOC]]<br>
Cover ::

# Evergreen Note

Question :: 題目來源-題目名稱

Answer ::Leetcode - 905. Sort Array By Parity

---

# Summary 
Given an integer array `nums`, move all the even integers at the beginning of the array followed by all the odd integers.
===給一個正整數陣列，偶數在前，奇數在後進行排序===

Return _**any array** that satisfies this condition_.
===回傳一個符合這條件的陣列===
**Example 1:**

**Input:** nums = [3,1,2,4]
**Output:** [2,4,3,1]
**Explanation:** The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.

**Example 2:**

**Input:** nums = [0]
**Output:** [0]

**Constraints:**

-   `1 <= nums.length <= 5000`
-   `0 <= nums[i] <= 5000`


---

# 我的解題想法
因為這題沒有要求要使用in-place語法，所以我直接使用js的語法完成。
先判斷edge，如果陣列長度小於2，那就回傳原本的陣列即可。
宣告newAry為空陣列。
使用for迴圈遍歷原陣列，如果當前的值餘數為0，那代表他是偶數，就將這個值以unshift方式加入新陣列（unshift會加在陣列頭），slice方式刪除原陣列值；如果當前的餘數不等於0，那代表他是奇數，將這個值以push的方式加入新陣列（push會加在陣列尾）。
當迴圈結束後回傳新陣列。
```javascript
var sortArrayByParity = function(nums) {
    if(nums.length < 2) return nums;
    let newAry = [];
    for(let i = 0; i < nums.length; i++){
        if(nums[i] % 2 === 0) {
            newAry.unshift(nums[i]);
            nums.slice(i,1);
        } else {
            newAry.push(nums[i]);
            nums.slice(i,1);
        }
    }
    return newAry;
};```
時間複雜度應該是O(n) ? 

---

# 其他解題想法
1. 宣告兩個陣列，一個存放奇數，一個存放偶數，最後合併陣列。
   
```javascript
var sortArrayByParity = function(nums) {
  if (nums.length === 0) return;
  let evenAry = [];
  let oddAry = [];
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] % 2 === 0) {
      evenAry.push(nums[i]);
    } else {
      oddAry.push(nums[i]);
    }
  }
  evenAry.push(...oddAry)
    return evenAry;
```
2. 使用in-place方式，不額外宣告新陣列（新空間）。宣告變數start指針為陣列頭，宣告變數end指針為陣列尾，當start指到的值除以2餘數大於0且end指到的值餘數為0，表示arr[start]奇數arr[end]偶數，這兩個數要對調位置。先宣告變數tmp存放當前arr[start]的值，再將arr[end]的值賦值給arr[start]。如果沒有同時符合以上條件，那就移動指針，如果arr[start]除以2餘數等於0，代表當前指到的值是偶數，start可以往後遍歷，start ++；如果arr[end]除以2餘數不等於0，代表當前指到的值是奇數，end可以往前遍歷，end -- 
```javascript
var sortArrayByParity = function(nums) {
  if (nums.length === 0) return;
  let start = 0;
  let end = nums.length - 1;
  let tmp;
  while (start < end) {
    if (nums[start] % 2 > nums[end] % 2) {
      tmp = nums[start];
      nums[start] = nums[end];
      nums[end] = tmp;
    }
    if(nums[start] % 2 === 0) start ++ ;
    if(nums[end] % 2 === 1) end -- ;
  }
  return nums
};
```