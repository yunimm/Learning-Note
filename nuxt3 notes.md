### 大綱
- file system router 文件路由系統
- auto import components
- config 設置
	- 配置簡化路徑路徑設定
	- 配置載入 css 路徑設定
- 安裝 TailwindCSS
- routing 路由

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
>新增 `pages` 資料夾 `index` 相當於首頁`:/`， 若沒有建立 `index.vue` ，訪問首頁或者返回上一頁是會出現404錯誤
>路由資料夾更新時，應該重啟伺服器

