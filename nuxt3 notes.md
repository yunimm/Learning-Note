### 大綱
- 文件路由系統
- auto import components
- config設置
- 配置簡化路徑路徑設定
- 配置載入css路徑設定
- 安裝TailwindCSS

### 教學影片
- [Nuxt 3 CodewithGuillaume](https://www.youtube.com/@codewithguillaume)](https://www.youtube.com/playlist?list=PL8HkCX2C5h0XT3xWYn71TlsAAo0kizmVc)

### 補充資料
- [import { resolve } 語法說明](https://ithelp.ithome.com.tw/articles/10244351)
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
})
```