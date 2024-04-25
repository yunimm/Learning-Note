---
date : 2022-10-2623:17
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📺 <br>
Source URL :: [{React Forms Full Tutorial - Validation, React-Hook-Form, Yup}](https://www.youtube.com/watch?v=UvH70UkbyfE&t=450s) <br>
Author :: {教學名稱} <br>
Topics :: [[React MOC]] [[React Library]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer ::

---

# Summary 
##### 如何使用
```js
載入yup
import * as yup from 'yup';
import { yupResolver } from '@hookform/resolvers/yup';

const schema = yup.object().shape({
	//名字對應input name
	firstName:yup.string().required(),
	lastName:yup.string().required(),
	age:yup.number().min(18).max(99).positive().integer().required(),
	password:yup.string().min(4).max(16).required(),
	confirmPassword:yup.string().oneOf([yup.ref("password"), null])
	//驗證規則一樣，可以使用yup的reference語法,缺點是沒有自己的errormessage
	可以用其他方式繞過，例如
	{errors.confirmPassword && "password error"}
});

const {register, handleSubmit, errors} = useForm({resolve:yupResolver(schema)})
```
---

# Note