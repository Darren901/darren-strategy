# MCP 工具指南：讓 AI 幫你做更多事

> **MCP（Model Context Protocol）** 是一種讓 AI 連接外部工具的標準協定。
> 透過 MCP，AI 不再只是聊天，而是能直接操作瀏覽器、查資料庫、部署服務、掃描安全漏洞……

---

## 什麼是 MCP？

想像 AI 是一個超強的助理，但原本只能待在辦公室接電話。
裝了 MCP 之後，這個助理可以：

- 走到你的瀏覽器前幫你操作網頁
- 打開資料庫查詢資料
- 幫你送出 PR、部署網站
- 掃描你的程式碼有沒有安全漏洞

**一句話：MCP 讓 AI 從「聊天工具」變成「能動手做事的夥伴」。**

---

## 常用 MCP 工具清單

### 🌐 瀏覽器操作

#### Chrome DevTools MCP
讓 AI 直接控制 Chrome 瀏覽器。

**能做什麼：**
- 自動點擊、填表、截圖
- 抓取網頁資料（爬蟲）
- 測試網站功能（自動化測試）
- 監看 Console 錯誤與 Network 請求

**適合場景：** QA 測試、自動化操作、抓取競品資訊

---

### 🗄️ 資料庫

#### Neon MCP（PostgreSQL 雲端資料庫）
直接讓 AI 操作 Neon 雲端 PostgreSQL 資料庫。

**能做什麼：**
- 用自然語言查詢資料（不用寫 SQL）
- 建立資料表、修改欄位
- 快速建立測試用資料庫

**適合場景：** 後端開發、資料查詢、快速 Prototype

#### Supabase MCP
連接 Supabase（Firebase 的開源替代品），整合資料庫、身份驗證、儲存空間。

**能做什麼：**
- 操作資料庫與 Storage
- 管理使用者權限
- 讀寫 Realtime 資料

**適合場景：** 全端開發、需要快速建立後端的專案

---

### 🎨 設計

#### Figma MCP
讓 AI 讀取 Figma 設計稿，直接轉換成程式碼。

**能做什麼：**
- 解析設計稿的色彩、字體、元件尺寸
- 自動生成對應的前端程式碼
- 看到喜歡的 UI 模板，直接讓 AI 實作出來

**適合場景：** 設計轉前端、UI 開發提速

---

### 📚 文件查詢

#### Context7 MCP
讓 AI 查詢最新的官方技術文件與程式碼範例。

**能做什麼：**
- 取得最新版本的框架文件（React、Next.js、Spring Boot 等）
- 避免 AI 使用過時語法
- 直接在對話中取得正確的 API 用法

**適合場景：** 開發時查文件、學習新技術

#### Ref MCP
與 Context7 類似，但支援更多冷門或小眾的技術文件來源。

**適合場景：** 使用較少見的函式庫或框架時

---

### 🖼️ 圖片生成

#### Replicate MCP
透過 Replicate 平台呼叫各種 AI 圖片生成模型。

**能做什麼：**
- 文字生成圖片（Stable Diffusion、Flux 等）
- 圖片風格轉換
- 生成素材、示意圖

**適合場景：** 美術素材、行銷素材、快速示意圖

---

### 🚀 部署

#### Vercel MCP
讓 AI 幫你部署前端專案到 Vercel。

**能做什麼：**
- 一鍵部署 Next.js、React 等專案
- 查看部署狀態與 Log
- 管理環境變數

**適合場景：** 前端部署、快速上線

#### Zeabur MCP
台灣團隊開發的部署平台，支援多種語言與框架。

**能做什麼：**
- 部署後端服務（Node.js、Python、Java 等）
- 管理服務與資料庫
- 自動建立 CI/CD 流程

**適合場景：** 全端部署、後端服務上線

#### Cloudflare MCP
連接 Cloudflare 的各項服務。

**能做什麼：**
- 管理 DNS 設定
- 部署 Cloudflare Workers（邊緣運算）
- 管理 KV 儲存與 R2 物件儲存

**適合場景：** 需要 CDN、邊緣部署、全球加速的專案

---

### 💻 程式碼版本控制

#### GitHub MCP
讓 AI 直接操作 GitHub。

**能做什麼：**
- 開 Issue、建立 PR
- Clone 專案、查看 Commit 記錄
- 搜尋程式碼
- 審查 PR 並留下 Review 評論

**適合場景：** 日常開發流程、Code Review 輔助

---

### 💳 金流

#### Stripe MCP
讓 AI 幫你管理 Stripe 金流服務。

**能做什麼：**
- 建立商品與定價方案
- 查詢訂單與付款記錄
- 設定訂閱方案

**適合場景：** 電商、SaaS 產品收費

---

### 🧩 前端元件

#### ShadCN MCP
讓 AI 直接使用 ShadCN UI 元件庫建立前端介面。

**能做什麼：**
- 生成 ShadCN 風格的元件程式碼
- 快速組裝後台介面、表單、對話框
- 保持設計一致性

**適合場景：** React / Next.js 前端開發

---

### 🔒 資安

#### Semgrep MCP
靜態程式碼安全掃描工具。

**能做什麼：**
- 掃描 SQL Injection、XSS 等常見漏洞
- 支援多種語言（Java、Python、JS、Go 等）
- 在開發階段就發現問題，不等到上線

**適合場景：** 程式碼 Review、上線前安全檢查

---

## Gemini CLI 設定方式

Gemini CLI 的 MCP 設定檔位置：

```
~/.gemini/settings.json
```

### 設定範例

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": [
        "chrome-devtools-mcp@latest"
      ]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "你的_GitHub_Token"
      }
    },
    "neon": {
      "command": "npx",
      "args": [
        "-y",
        "@neondatabase/mcp-server-neon",
        "start",
        "你的_Neon_API_Key"
      ]
    },
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### 安裝前提

確認已安裝 Node.js（建議 v18 以上）：

```bash
node -v
npm -v
```

### API Key 取得方式

| MCP | 取得位置 |
|-----|----------|
| GitHub | GitHub → Settings → Developer settings → Personal access tokens |
| Neon | Neon Console → Settings → API Keys |
| Supabase | Supabase Dashboard → Project Settings → API |
| Replicate | replicate.com → Account Settings → API Tokens |
| Vercel | Vercel Dashboard → Settings → Tokens |
| Stripe | Stripe Dashboard → Developers → API Keys |
| Cloudflare | Cloudflare Dashboard → My Profile → API Tokens |

---

## 建議入門組合

剛開始不需要裝全部，依使用情境選擇：

| 情境 | 建議安裝 |
|------|----------|
| 後端開發 | GitHub + Neon/Supabase + Context7 |
| 前端開發 | GitHub + Figma + ShadCN + Vercel |
| 全端開發 | GitHub + Supabase + Context7 + Vercel/Zeabur |
| 資安 / Code Review | GitHub + Semgrep |
| 自動化測試 | Chrome DevTools |

---

## 注意事項

1. **API Key 請妥善保管**，不要提交到 Git Repository
2. MCP 工具賦予 AI 實際操作權限，**請確認 AI 的操作符合預期再執行**
3. 使用資料庫相關 MCP 時，**建議先在測試環境操作**，避免誤改正式資料
4. 部分 MCP 工具需要付費帳號（如 Neon、Replicate、Stripe）

---

*文件版本：2026-02-26*
