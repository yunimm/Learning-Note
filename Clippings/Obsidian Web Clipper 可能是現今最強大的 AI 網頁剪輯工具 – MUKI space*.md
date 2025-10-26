---
title: "Obsidian Web Clipper 可能是現今最強大的 AI 網頁剪輯工具 – MUKI space*"
source: "https://muki.tw/obsidian-web-clipper-ai-tool/"
author:
  - "[[MUKIwu]]"
  - "[[Follow Me]]"
published:
created: 2025-10-26
description:
tags:
  - "clippings"
---
![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-12.11.12-960x560.png "Obsidian Web Clipper 可能是現今最強大的 AI 網頁剪輯工具")

[數位筆記生活](https://muki.tw/planner/digital-note-taking/ "數位筆記生活")

## Obsidian Web Clipper 可能是現今最強大的 AI 網頁剪輯工具

By

3.2K

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-12.11.12-940x1024.png)

我最近發現 Obsidian 官方推出了一個專用的 Web Clipper 工具，試用之後認為它是現今最強大的 AI 網頁剪輯工具之一。這個工具不僅操作簡單，還能夠輕鬆地將網頁內容整理成我需要的格式，讓我的筆記變得更加有條理。

他不僅免費，還支援高度客製化與強大的 AI 功能，對於想提升知識管理效率的朋友來說，絕對值得一試！

## 為什麼選擇 Obsidian Web Clipper？

以前我使用的是 Readwise Highlighter 幫我剪輯後放到 Readwise 中，但我的 Readwise 將於今年五月到期，暫時不再續訂，而且 Readwise Highlighter 的客製化稍嫌不足，我還是希望可以 **(1)更自動 (2)更客製化** ，所以我找到了 Obsidian Web Clipper。

Obsidian Web Clipper 是一款專為 Obsidian 設計的瀏覽器擴充工具。他能讓我們快速從瀏覽器中剪輯網頁內容，並將其保存到 Obsidian 的筆記庫中，不僅能幫助我們快速收集資料，還能促進知識的整合與管理。

Obsidian Web Clipper 的特色簡易整理如下：

- 所有的檔案都會存成 markdown 文件，並存在你的本地資料夾
- 支援任何格式的網頁排版 (含圖片、影片、表格... 等版面格式，文章還能抓到引用和註腳)
- 支援高亮
- 可以設定 AI Prompt 自定義樣板，與分析你截取的文章內容
- 有針對如 Youtube, Twitter, Podcast、食譜、電影、書籍... 等版面的處理，可以完美儲存相關資訊

## 安裝與基本設定

事前準備：Obsidian 筆記軟體

套件建議搭配 Obsidian 軟體，這是一個免費又好用的筆記軟體，請點我下載

**1\. 安裝擴充工具**

如果你是用 Chorme 瀏覽器，可以到 Chrome Extension [安裝 Obsidian Web Clipper](https://chromewebstore.google.com/detail/obsidian-web-clipper/cnjifjpddelmedmihgijeibhnjfabmlf) ，其他的瀏覽器請到官網 [選擇安裝](https://obsidian.md/clipper#more-browsers)

**2\. 設定語言**

對著擴充工具按「右鍵」→「選項」進入設定畫面，可以先將語言設定為「繁體中文」

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.22.38.png)

**3\. 設定儲存的資料夾**

我們可以在 Obsidian Web Clipper 設定多個範本，也可用預設(Default)的做修改，點選「Default」選擇預設的範本後，找到「筆記位置」，填入你想儲存筆記的資料夾或路徑 (預設的資料夾名稱為 Clippings，接受中文)

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.25.11.png)

如果沒有要使用 AI，只是單純要剪輯網頁，設定到這邊就可以了。

可以對著要剪輯的網頁按下 Obsidian Web Clipper 服務，會先提供預覽再選擇要不要存檔。

▼ 以 Youtube 為例，剪輯的資訊蠻完整的，有需要也可以自行擴充定義樣板

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.29.31-1024x653.png)

▼ 有使用沉浸式翻譯的朋友，Obsidian Web Clipper 也能一併將翻譯剪過來

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-14.02.36-1024x436.png)

## 使用 AI 自動產生摘要與定義 prompt

Obsidian Web Clipper 最吸引人的地方在於它的 AI 整合能力。

**1\. 設定 AI 模型**

選擇「解譯器」加入 AI 與他的模型，我使用的是 Google Gemini

▼ 點擊「新增提供者」新增 AI 服務與 API 金鑰，預設就提供了許多知名的 AI 服務，也可以自訂，所以我們也能使用本機的 AI 服務唷！

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.32.56.png)

▼ 新增模型

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.35.01.png)

**2\. 自定義範本與 Prompt**

再來選擇你要用的範本 (這邊以 Default) 為例，我們可以直接在變數中執行 Prompt。

例如截取的網站標題如果是英文，我希望能透過 AI 自動翻譯成中文，原本的網站標題變數是 `{{ title }}` ，我可以 prompt 改寫成 `Obsidian Web Clipper 可能是現今最強大的 AI 網頁剪輯工具` ，這段話的意思是告訴 AI 將標題翻譯成繁體中文並回傳

▼ 設定完成後，截取網頁時會執行 AI，等 AI 執行完畢，就能看到我截取的英文網頁自動將標題翻譯成繁體中文

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.40.30.png)

**3\. 自訂摘要與其他應用**

▼ 除了標題外，也可以在筆記內容呼叫 AI，我使用的 prompt 是 `Obsidian Web Clipper 是一款為 Obsidian 設計的免費瀏覽器擴充工具，可快速將網頁內容剪輯並保存為 Markdown 格式到本地筆記庫。該工具支援任何網頁排版格式（含圖片、影片、表格等），並提供高亮功能。其核心優勢在於強大的 AI 整合能力，用戶可設定 Google Gemini 等 AI 模型來自動翻譯標題、產生摘要及自訂內容分析。透過自定義 Prompt 和範本系統，用戶可針對 YouTube、Twitter、Podcast 等不同網站類型自動應用對應模板，大幅提升知識管理效率和內容整理品質。` ，請 AI 摘要文章並回傳繁體中文，也可以適當用 Markdown 語法排版

Markdown

```
xxxxxxxxxx
```

6

1

```
## 摘要
```

2

```
Obsidian Web Clipper 是一款為 Obsidian 設計的免費瀏覽器擴充工具，可快速將網頁內容剪輯並保存為 Markdown 格式到本地筆記庫。該工具支援任何網頁排版格式（含圖片、影片、表格等），並提供高亮功能。其核心優勢在於強大的 AI 整合能力，用戶可設定 Google Gemini 等 AI 模型來自動翻譯標題、產生摘要及自訂內容分析。透過自定義 Prompt 和範本系統，用戶可針對 YouTube、Twitter、Podcast 等不同網站類型自動應用對應模板，大幅提升知識管理效率和內容整理品質。
```

3

```
​
```

4

```
## 原文
```

5

```
​
```

6

```
{{content}}
```

![](https://muki.tw/wordpress/wp-content/uploads/2025/04/CleanShot-2025-04-08-at-13.45.13.png)

如果想要知道還有哪些變數可以使用？都可以到 [Obsidian 的官方文件](https://help.obsidian.md/web-clipper/variables) 觀看喔。

## 更多的範本 Templates

Obsidian Web Clippers 可以根據要剪輯的網址(網域)自動使用不同的範本，所以網路上也有一些特定網站的範本可參考，例如 Google Maps, GitHub, IMDB.... 等等，以下分享兩個範本位置，大家可以參考看看

### Kepano

clipper-templates： [https://github.com/kepano/clipper-templates](https://github.com/kepano/clipper-templates)

支援的網站範本：

- [Arxiv](https://github.com/kepano/clipper-templates/blob/main/templates/arxiv-clipper.json)
- [Goodreads](https://github.com/kepano/clipper-templates/blob/main/templates/goodreads-clipper.json)
- [Google Maps](https://github.com/kepano/clipper-templates/blob/main/templates/google-maps-clipper.json)
- [IMDB](https://github.com/kepano/clipper-templates/blob/main/templates/imdb-clipper.json)
- [IMDB (reference view)](https://github.com/kepano/clipper-templates/blob/main/templates/imdb-reference-clipper.json)
- [Letterboxd](https://github.com/kepano/clipper-templates/blob/main/templates/letterboxd-clipper.json)
- [Redfin](https://github.com/kepano/clipper-templates/blob/main/templates/redfin-clipper.json)
- [Wikipedia](https://github.com/kepano/clipper-templates/blob/main/templates/wikipedia-clipper.json)
- [Youtube](https://github.com/kepano/clipper-templates/blob/main/templates/youtube-clipper.json)

### Obsidian Community

templates： [https://github.com/obsidian-community/web-clipper-templates/tree/main/templates](https://github.com/obsidian-community/web-clipper-templates/tree/main/templates)

如果你有很棒的 idea，也可以發 PR 請求合併，目前有：

- Apple Podcast
- GitHub
- Reddit
- The Hacker News
- Youtube

## 小結

Obsidian Web Clipper 是一款功能強大的網頁剪輯工具，適合各類型的知識工作者使用。無論是學術研究、內容創作還是日常筆記，它都能幫助我們大幅提升內容整理的效率和品質，歡迎加入 Obsidian 的行列，一起提升工作與學習的效率吧！

以上，有任何問題，都歡迎留言討論唷。