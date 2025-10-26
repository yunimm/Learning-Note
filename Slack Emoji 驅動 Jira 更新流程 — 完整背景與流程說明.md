## 1. 專案背景
我們的產品由三個專案組成：
- **一個 SPA 專案**
- **兩個 SSR 專案**

同一個需求的範圍（scope）有時需要跨三個專案協作，因此團隊內建立了一個 **版本紀錄文件**，用來追蹤每次版本更新號碼及對應的 Jira ticket。

---

## 2. 問題與需求
- 版本紀錄與 ticket 狀態更新完全依賴人工操作，每次手動記錄與更新耗費大量時間。
- 產品工程師（PE）需要根據我們的版本：
  - 更新 WordPress
  - 切換 Jira ticket 狀態
  - 在 ticket 中留言版本號碼
- 手動操作繁瑣且容易出錯，效率低下。

**因此，我被要求設計一個自動化方案**，希望能同時提升跨專案協作效率並減少人工操作。

---

## 3. 自動化解決方案概述
為了達成目標，我規劃了 **Slack Emoji 驅動 Jira 更新流程**，核心設計如下：

### 3.1 Release Notes 自動化
- 從 **GitHub CI/CD workflow** 收集每次版本號與對應 ticket
- 自動生成 release notes，並透過 Slack 發佈至指定頻道

### 3.2 Emoji 觸發流程
- 使用者對 release notes 訊息加 emoji
- 透過 Make 或 Workflow Builder 監聽 emoji 事件
- 根據 emoji 類型，決定後續動作：
  - 自動更新 Jira ticket 狀態
  - 在 ticket 中留言版本號碼
  - 處理不同專案或 hotfix 情境

### 3.3 彈性與擴展性
- 流程設計支援 **多專案協作**（SPA 與 SSR）
- 支援 **不同情境分支**（如 hotfix 或版本回滾）
- 發訊息與後續更新分離，降低操作錯誤風險
- 可延伸到其他自動化整合需求

---


## 4. 流程概念圖（Mermaid）

```mermaid
flowchart TD
    A[GitHub CI/CD 完成 Release] --> B[Slack 發 Release Notes 訊息]
    
    B --> C1[主管 Bot Token]
    C1 --> D1[只能發訊息 ✅]
    D1 --> E1[無法讀 emoji ❌]

    B --> C2[個人帳號授權 Make]
    C2 --> D2[可發訊息 ✅]
    D2 --> F2[監聽 emoji ✅]
    F2 --> G2[Make 觸發 Jira 更新 ✅]

    B --> C3[Workflow Builder + Make Webhook]
    C3 --> D3[Workflow detect emoji ✅]
    D3 --> F3[呼叫 Make Webhook]
    F3 --> G3[Jira 更新 ✅]
