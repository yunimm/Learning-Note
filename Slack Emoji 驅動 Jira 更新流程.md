## 目標
- 發佈 Release Notes → Slack 訊息  
- 使用者在訊息加 emoji → 觸發自動化 → 更新 Jira ticket

---

## 方案比較表

| 方案                                  | 權限來源           | 可發訊息            | 可讀 emoji                | 可監聽事件               | 可更新 Jira | 優缺點                                   |
| ----------------------------------- | -------------- | --------------- | ----------------------- | ------------------- | -------- | ------------------------------------- |
| **主管 Bot Token**                    | 主管提供的 bot      | ✅ `chat:write`  | ❌                       | ❌                   | ⚠️ 需額外授權 | 優點：已可發訊息；缺點：無法讀 emoji，不可觸發自動化         |
| **個人 Slack 帳號授權 Make**              | 自己公司帳號         | ✅               | ✅ `reactions:read`      | ✅                   | ✅        | 優點：可監聽 emoji、觸發 Jira 更新；缺點：需自己授權 Make |
| **Workflow Builder + Make Webhook** | Slack Workflow | ⚠️ Workflow 發訊息 | ✅ Workflow detect emoji | ✅ call Make webhook | ✅        | 優點：不需改 bot 權限；缺點：需多一步 Workflow 設定     |

---

## 建議方案
1. **快速上手 / 簡單彈性** → 用 **個人帳號授權 Make**  
2. **公司政策嚴格 / 禁止個人整合** → 用 **Workflow Builder + Make Webhook**  
3. **現有主管 Bot Token** → 只能用於發訊息通知，無法做互動觸發 Jira

---

## 流程概念圖（Mermaid）

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