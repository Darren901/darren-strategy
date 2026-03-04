# AI Agent Charter (AI 代理憲章)

## ⚠️ 關鍵指令

**必須使用繁體中文 (Traditional Chinese) 與使用者溝通。**
所有解釋、對話、問題確認都必須使用繁體中文。程式碼註解可使用英文或繁體中文。

**實作任何功能或 Bug Fix 的強制順序（無例外）：**
1. 禁止在呼叫 `tdd-workflow` Skill 之前使用 Write 或 Edit 工具修改任何程式碼
2. 禁止在呼叫 `superpowers:test-driven-development` Skill 之前開始實作
3. 違反以上兩點視為流程錯誤，必須立即停止並重新執行正確順序

---

## 專案背景

**Project**: [專案名稱 - 請在此填入]
**Description**: [專案描述 - 請在此填入]
**開發模式**: [綠地 Greenfield / 褐地 Brownfield]

**Tech Stack**:

- Java 21（請根據專案調整）
- Spring Boot 3.x（請根據專案調整）
- Database: [PostgreSQL / MySQL / MS SQL 等]
- Cache: [Redis / Caffeine / None]
- Additional: [Spring AI / GraphQL / Kafka 等]

---

## 常用命令

```bash
mvn clean compile   # 編譯驗證
mvn test            # 執行測試
mvn spring-boot:run # 啟動應用程式
```

---

## 專案結構

```
src/main/java/com/example/
├── controller/   # REST API 入口
├── service/      # 業務邏輯
├── repository/   # 資料存取
├── domain/       # Entity / Value Object
├── dto/          # Request / Response DTOs
└── config/       # Spring 配置類
```

---

## 禁止事項

- 禁止 field injection（`@Autowired` on fields）
- 禁止 wildcard import（`import java.util.*`）
- 禁止將密碼、API keys、token 寫入程式碼或 log
- 禁止直接修改已發布的 Flyway migration 檔案（如使用 Flyway）
- 禁止在 Controller 直接操作 Entity，必須經過 DTO（如使用 JPA）

---

## 對話規範

### Understand（每次對話開始時）

先閱讀以下檔案再行動：

- `README.md` — 了解專案概觀（如存在）
- `pom.xml` / `build.gradle` — 確認 Tech Stack 與依賴版本
- `application.yml` — 確認環境配置

褐地開發時額外進行影響分析，再進入 `brainstorming`。

### Communicate（每次完成後）

必須用**繁體中文**輸出：做了什麼（What）、為什麼這樣設計（Why）、需確認的問題（若有）、已知限制或後續建議（若有）。

---

## 規則文件

詳細規範請參考 `.claude/rules/`：

- `code-style.md` — 程式碼風格、命名規範、Logging、程式碼文件
- `architecture.md` — 分層架構、設計模式（Template/Strategy/Observer）
- `api-design.md` — URL 命名、HTTP Methods/Status Codes、統一 Response 格式
- `config-security.md` — 配置管理、安全最佳實踐
- `database.md` — 資料庫設計、Migration、查詢優化
- `performance.md` — 效能考量（DB 連接池、快取、API 分頁）
- `git.md` — Git Workflow、Commit Message 格式
- `testing.md` — 強制 TDD 規則、兩個 TDD Skill 分工、覆蓋率要求
- `workflow.md` — 工具選型原則、綠地/褐地完整開發流程

---

## 工作流規範

依任務規模選擇對應流程，**不得過度設計**。詳細流程見 `.claude/rules/workflow.md`：

| 規模 | 判斷標準 | 流程 |
|---|---|---|
| **小型** | 單一方法修改、簡單 bugfix | 直接實作 → `verification-before-completion` |
| **中型** | 新增單一功能、修改一個模組 | 視開發模式選擇（見 workflow.md） |
| **大型** | 新系統、跨模組重構、重大功能 | 視開發模式選擇（見 workflow.md） |

**所有功能實作與 Bug Fix 禁止跳過 TDD 流程。詳見 `.claude/rules/testing.md`。**
