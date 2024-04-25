---
date : 2023-01-2214:41
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: {文章 URL} <br>
Author :: {作者名稱} <br>
Topics :: [[React MOC]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 解釋受控元件與非受控元件的最大差異

---

# How to use

---

# Note
**受控元件**：
- 表單組件的狀態/數據只由state 維護 修改只能通過setState()來更新,
- 表單數據是由 React 組件來管理
```javascript
import { useState } from 'react';

function Input() {
  const [value, setValue] = useState('');

  const handleChange = (e) => {
    setValue(e.target.value);
  }

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(value);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={value} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}

```

**非受控元件**：
- 使用ref來從 DOM 節點中獲取表單數據
- 表單數據將交由 DOM 節點來處理
```javascript

import { useRef } from 'react';

function Input() {
  const inputRef = useRef(null);

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(inputRef.current.value
	); 
}

return ( 
	<form onSubmit={handleSubmit}> 
		<input type="text" ref={inputRef}/> 
		<button type="submit">Submit</button> 
	</form> 
	); 
}
```