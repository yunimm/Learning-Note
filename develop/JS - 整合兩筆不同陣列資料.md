---
date : 2022-05-1209:22
aliases : []
---
# Metadata
Status :: #ð± <br>
Note Type :: #ð¨/ð¿ <br>
Source URL :: [è³ææ´ååç½®ä½æ¥­ - æ´åæ¹æ³ä¸ (5:03)](https://courses.hexschool.com/courses/the-f2e-js/lectures/37105983) <br>
Author :: [[@å­è§]] <br>
Topics :: [[-Javascript moc]] [[-è³æèç moc]] [[JSé£åæä½ moc]] <br>
Cover ::

# Evergreen Note

Question :: éç¯æç« ä¸»è¦å¨èªªä»éº¼ ?

Answer ::

---

# Summary 

---

# Note
åè¨­ä»å¤©æå©çµä¸åçè³æéè¦æé¸åºéè¦çè³æä¸¦ä¸å½æ´ææ°çè³æï¼å¯ä»¥ä½¿ç¨forEachçæ¹å¼å»è§£
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
	school: 'ABCé«ä¸­',
},
{
	name: 'Peter',
	school: '123åä¸­'

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