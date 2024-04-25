### 大綱
- file system router 文件路由系統
- auto import components
- config 設置
	- 配置簡化路徑路徑設定
	- 配置載入 css 路徑設定
- 安裝 TailwindCSS
- routing 路由
	- navigation 導覽列
	- useRoute 
- useNuxtApp()

### 教學影片
- [Nuxt 3 CodewithGuillaume](https://www.youtube.com/@codewithguillaume)](https://www.youtube.com/playlist?list=PL8HkCX2C5h0XT3xWYn71TlsAAo0kizmVc)

### 補充資料
- [import { resolve } 語法說明](https://ithelp.ithome.com.tw/articles/10244351)

--- 
#### nuxt.config.ts
[官方文件設定說明](https://nuxt.com/docs/api/configuration/nuxt-config)
```typescript
// https://nuxt.com/docs/api/configuration/nuxt-config

import { resolve } from "path";//簡化載入路徑
export default defineNuxtConfig({

devtools: { enabled: true },
	alias:{
	"@": resolve(__dirname, "/"),
	},
	css:["~/assets/main.scss"], //配置css載入路徑
})
```

#### routing
[官方文件設定說明](https://nuxt.com/docs/getting-started/routing)
在nuxt建立路由不同於vue，是用文件夾的方式設定，文件夾的關聯性相當於路由的關聯，例如要建立巢狀路由就是在資料夾內再開一個資料夾
```

pages/
--| about.vue
--| index.vue
--| posts/
----| [id].vue

```
##### navigation
使用 `<NuxtLink to="{route}">` 取代 `a`  
```vue
<template>
	<h1>this is index</h1>
	<ul>
		<li><NuxtLink to="/about">About</NuxtLink></li>
		<li><NuxtLink to="/aa">aa</NuxtLink></li>
	</ul>
</template>

```
##### useRoute
使用 `useRoute` 可以取得路由裡的參數
```vue
<script setup>

const route = useRoute();

console.log(route.params);

</script>
```
>新增 `pages` 資料夾 `index` 相當於首頁`:/`， 若沒有建立 `index.vue` ，訪問首頁或者返回上一頁是會出現404錯誤
>路由資料夾更新時，應該重啟伺服器



#### useNuxtApp()
在component內使用Nuxt內建的屬性或是方法，例如：
1. `$config`: 用於取你的公共運行時配置（publicRuntimeConfig 和 privateRuntimeConfig）。
2. `$fetch`: Nuxt.js 提供了一個用於數據獲取的 Hook。
3. `$cookies`: 提供了一種在服務器端和客戶端管理 cookies 的方式。
4. `$nuxt`: 這個對象包包含了一些用於控制Nuxt.js 應用程序的方法，例如`$nuxt.refresh()`可以用於強製造新頁面。
5. `$route`和`$router`:`$route`是一個包含了當之前路由信息的對象，`$router`是Vue Router實例。
6. `$store`: 如果你的應用程序使用了 Vuex，`$store`就是 Vuex Store 的實例。
7. `$head`: 這是一個函數，可以使用動態更新`<head>`標籤的內容。
8. `$url`: 這個對象提供了一些工具方法，比如`$url.join()`，可以使用來處理URL。
```vue
<script setup>
const nuxt = useNuxtApp();
console.log(nuxt);
</script>
```