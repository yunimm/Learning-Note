---
date : 2022-09-1114:44
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️  +  💿  <br>
Source URL :: {教學 URL} <br>
Author :: 

Topics :: {筆記跟什麼主題有關，用`[Topic],[Topic]` 格式} <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
##### 如何使用
- 使用 **布林值** 控制input是否被勾選
```jsx
function LoginForm() {

	const [check, setCheck] = useState(false);
	
	return (
	
		<div>
		
			<input
			
			type="radio"
			
			value="123"
			
			checked={check}
			
			onChange={(e) => {setCheck(true);}}
			
			/>
			
			123
			
			<input
			
			type="radio"
			
			value="456"
			
			checked={!check}
			
			onChange={(e) => {setCheck(true);}}
			
			/>
			
			456
			
		</div>
	
	);

}
```
- 在return時比對當前`value`值和`state`是否相同，如果相同表示true(被勾選)反之false(取消勾選)
```jsx
	
```
---

# Note