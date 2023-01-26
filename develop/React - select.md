---
date : 2022-09-0922:55
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📚️  +  💿  <br>
Source URL :: {教學 URL} <br>
Author :: [[@AC - ReactBeta]] [[@React思考模式]]<br>
Topics :: [[-React Moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: `<select>` 的用法

---

# Summary 
##### 如何使用
- 在React中，一般使用`selected`標示被選取的`option`，而是使用value
```jsx
	function LoginForm() {

	const [nowSelect, setNowSelect] = useState('');
	
	return (
	
		<select value={nowSelect} onChange={(e)=>{setNowSelect(e.target.value)}}>
		
		<option value="grapefruit">Grapefruit</option>
		
		<option value="lime">Lime</option>
		
		<option selected value="coconut">
		
		Coconut
		
		</option>
		
		<option value="mango">Mango</option>
		
		</select>
	
	);

}
```
另一種方式是綁`selected` (布林值)，如果`select`有綁定`value`、`defalutValue`則以`select`為主
```jsx
	<select onChange={(e)=>{setNowSelect(e.target.value)}}>

	<option value="grapefruit">Grapefruit</option>
	
	<option value="lime">Lime</option>
	
	<option selected={true} value="coconut">
	
	Coconut
	
	</option>
	
	<option value="mango">Mango</option>
	
	</select>
```
- 如果`select`綁定的`value`值不為當前`option`的任一個值，則顯示第一個`option`
- 取得`<select>` 被選取的值是用`onChange`不是用`onClick`
- 使用`onChange`觸發修改事件並使用`setState`改變`state` 
```jsx
	<select 
		onChange={(event)=>{/* 用event.target.value去setState */}}> 
    </select>
```
- 使用`useState` 紀錄選取的值和改變的方法
```jsx
	const [nowSelect, setNowSelect] = useState('');
```
- 將`state`綁定在`value`
```jsx
	<select value={nowSelect}></select>
```


---

# Note
