---
date : 2023-01-2214:41
aliases : []
---
# Metadata
Status :: #🌱 <br>
Note Type :: #📨/📝 <br>
Source URL :: {文章 URL} <br>
Author :: {作者名稱} <br>
Topics :: [[-React Moc]]<br>
Cover ::

# Evergreen Note

Question :: 這篇文章主要在說什麼 ?

Answer :: 解釋受控元件與非受控元件的最大差異

---

# How to use

---

# Note
**受控元件**：由React使用value屬性和onChange事件更新元件狀態，元件狀態會和DOM同步
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

**非受控元件**：React只負責渲染，依照使用者的操作行為更新元件狀態，元件狀態不會和DOM同步
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