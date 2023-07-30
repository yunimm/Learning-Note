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
4. 比對數字
5. 比對字串
6. 實作電話簿查找功能
7. Sorting
8. Selection Sort
9. Bubble Sort
10. Merge Sort
11. Recursion
---

# Note
#### Linear Search
假設當前有七個置物箱，每個置物箱裡都有一張鈔票，我們要尋找存放鈔票面額為50的置物箱，該怎麼找？(每個置物箱的鈔票並沒有按照排序存放)
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

#### Binary Search
假設當前有七個置物箱，每個置物箱裡都有一張鈔票，我們要尋找存放鈔票面額為50的置物箱，該怎麼找？(每個置物箱的鈔票按照排序存放)
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

#### 在 C 實踐線性搜尋
##### 比對數字
```c
#include <cs50.h>
#include <stdio.h>
 
int main(void)

{

	int numbers[] = {20,100,5,200,1,50};
	int n = get_int("Number:");

	for(int i = 0; i < 7; i++)

	{

		if(numbers[i] == n)

		{

			printf("Found\n");
			return 0;

		}

	}

	printf("Not found\n");

	return 1;

}
```
##### 比對字串
- 使用strcmp函式庫比對字串
- 可以使用 `echo $?` 查看return 的結果，
- 
- 
- 通常來說，如果該程序成功執行，則 `$?` 會返回0，否則返回非0值。
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

  
int main(void)

{

	string strings[] = {"battleship", "boot", "cannon", "iron", "thimble", "top hat"};
	string s = get_string("String:");
	
	for(int i = 0; i < 6; i++)
	
		{
		
				if(strcmp(strings[i], s) == 0)
		
			{
		
				printf("Found\n");
				
				return 0;
			
			}
		
		}
	
	printf("Not found\n");
	
	return 1;


}
```
實作
#####  實作電話簿查找功能
- 結合前兩個範例實作看看
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

  

int main(void)

{

	string names[] = {"mike", "amy"};
	
	string numbers[] = {"+886-0912345678", "+886-0932112345"};
	
	  
	
	string name = get_string("Name: ");
	
	for(int i = 0; i < 2; i++)
		
		{
		
			if(strcmp(names[i],name) == 0)
		
			{
		
				printf("Founs %s\n", numbers[i]);
				
				return 0;
		
			}
		
		}
		
	printf("Not found\n");
	
	return 1;

}
```
#### 上述程式碼有沒有辦法更好？或是說有哪裡需要改進的嗎？
- 如果今天names增加了，但是電話號碼沒有一起增加，是不是會找不到電話？
- 迴圈目前是寫死的數字(2)，是不是可以替換成變數？
- 要怎麼證明我這次比對到的名字就是這組號碼呢？會不會有因為新增號碼或名字後對應排序亂掉的問題呢？
##### 我們可以用c的自定義資料結構解決這個問題（有點類似先用TS的interface先定義出型別）：
```c
#include <cs50.h>

#include <stdio.h>

#include <string.h>

  

typedef struct //固定語法

{
//自訂義預設資料型別，但不能帶入預設值

string name;

string number;

}

person; //自訂上次型別名稱

  

int main(void)

{

  

person people[2]; //宣告陣列長度二的資料，型別是person

people[0].name = "mike";
people[0].number = "+886-234-6544";

people[1].name = "alex";
people[1].number = "+886-111-2323";

string name = get_string("Name: ");

for(int i = 0; i < 2; i++)

{

	if(strcmp(people[i].name,name) == 0)
	
	{
	
		printf("Founs %s\n", people[i].number);
		
		return 0;
	
	}

}

printf("Not found\n");

return 1;

}
```

#### Sorting
##### Selection Sort 選擇排序法
1. 找出數據結構中的最小值。
2. 把最小值和數據結構中的第一個元素交換位置。
3. 在剩下的元素中找出最小值，然後把這個最小值與第二個元素交換位置。
4. 這個過程一直持續，直到進行到數據結構的最末端。
##### Bubble Sort
1. 比較相鄰的元素。如果第一個比第二個大，就交換它們兩個。
2. 對每一對相鄰元素作同樣的工作，從開始第一對到結尾的最後一對。這步做完後，最後的元素會是最大的數。
3. 針對所有的元素重複以上的步驟，除了最後一個。
4. 持續每次對越來越少的元素重複上面的步驟，直到沒有任何一對數字需要比較
。
##### Merge Sort
如果陣列長度=

#### Recursion
它是指一個函數直接或間接地呼叫自身一次或多次的過程。換句話說，函數在執行時會再次呼叫自己，以解決較小或更簡單的子問題。
使用先前的Binary Search 當範例，程式碼內的`Search left/right half` 就是遞迴的元素，如果< / > 50 就進行搜尋，不斷地把問題切小，直到找到 / 搜尋範圍結束為止
```js
If no door left 
	Return false 
If 50 is behind middle door
	Return true
Else if 50 < middle door
	Search left half ->
Else if 50 > middle door
	Search right half -> 
```
##### 使用遞迴修改前幾週的印馬力歐程式碼
原本使用雙迴圈：
```c
#include <cs50.h>
#include <stdio.h>

void draw(int n);
int main(void)
{
	int height = get_int("height: ");
	draw(height);
}

void draw(int n)
{
	for(int i = 0; i < n; i++)
	{
		for(int j = 0; j < i + 1; j++)
		{
			printf("#");
		}
		print("\n");
	}
}
```
使用遞迴實現：
```c
#include <cs50.h>
#include <stdio.h>

void draw(int n);
int main(void)
{
	int height = get_int("height: ");
	draw(height);
}

void draw(int n)
{
	if(n <= 0)
	{
		return;
	}

	draw(n-1);
	
	for(int i = 0; i < n; i++)
	{
		printf("#");
	}
	print("\n");
}
--------------------------------------------------------------------------------------

//遞迴實踐過程：
//都呼叫完了draw之後，會呈現一層包一層的程式碼，由最裡層一層一層執行到外面，所以最後印出結果會是
#
##
###
void draw(3) {
	draw(2) {
		draw(1) {
			draw(0) {
			// 終止遞迴
			}
		// 打印一個 '#'
		}
	// 打印兩個 '#'
	}
// 打印三個 '#'
}
```