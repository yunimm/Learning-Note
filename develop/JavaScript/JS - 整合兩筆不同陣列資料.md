---
date : 2022-05-1209:22
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/💿 <br>
Source URL :: [資料整合前置作業 - 整合方法一 (5:03)](https://courses.hexschool.com/courses/the-f2e-js/lectures/37105983) <br>
Author :: [[@六角]] <br>
Topics :: [[JavaScript MOC]] [[DataProcessing MOC]] [[JS陣列操作 moc]] <br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 

---

# Note
假設今天有兩組不同的資料需要挑選出需要的資料並且彙整成新的資料，可以使用forEach的方式去解
```
const users = [
{
	id: 1,
	name: 'Amy',
	age: '19'
},
{
	id: 2,
	name: 'Peter',
	age: '13'
}]
const students = [
{
	name: 'Amy',
	school: 'ABC高中',
},
{
	name: 'Peter',
	school: '123國中'

}] 

const newData = []

function mixData() {
  	users.forEach((user) => {
		students.forEach((student) =>{
			if(user.name === student.name) {
				let obj = {
					id: user.id,
					name: user.name,
					age: user.age,
					school: student.school
				}
				newData.push(obj)
			}
		})
	})
  console.log(newData)
}

mixData()


```