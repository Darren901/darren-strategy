# Darren's AI Strategy

這個倉庫收錄了我在使用 Claude Code 過程中整理出的 **工作流策略、規範文件、Skills 與 Custom Commands**，供參考與複製使用。

---

## 目錄結構

```
darren-strategy/
├── CLAUDE.md               # AI 代理憲章（核心規範，放到專案根目錄使用）
├── mcp-guide.md            # MCP 伺服器安裝與設定指南
├── presentation.html       # AI 工作流分享 - 簡報（在瀏覽器開啟）
├── commands/               # Custom Commands（複製到 ~/.claude/commands/）
│   ├── verify.md           # /verify：一鍵執行編譯 + 測試 + 覆蓋率驗證
│   └── learn.md            # /learn：從 session 提取知識並存入記憶
├── skills/                 # Claude Skills 集合
│   ├── tdd-workflow/       # TDD 工作流：Red-Green-Refactor（Java Spring Boot）
│   ├── frontend-design/    # 前端設計：生成高品質 UI 介面
│   ├── canvas-design/      # Canvas 設計：生成海報、視覺藝術
│   ├── writing-skills/     # 寫作輔助：撰寫/驗證 Skills
│   ├── skill-creator/      # Skill 建立嚮導
│   ├── mcp-builder/        # MCP 伺服器建立指南
│   ├── webapp-testing/     # Web App 測試（Playwright）
│   ├── internal-comms/     # 內部溝通文件撰寫
│   ├── doc-coauthoring/    # 文件共同撰寫工作流
│   ├── pdf/                # PDF 處理
│   ├── docx/               # Word 文件處理
│   ├── pptx/               # PowerPoint 處理
│   ├── xlsx/               # Excel 處理
│   └── agent-skills-code-review-router/  # Code Review 路由
└── .claude/
    └── rules/              # 詳細規範（放到 .claude/rules/ 使用）
        ├── code-style.md       # 程式碼風格、命名規範
        ├── architecture.md     # 分層架構、設計模式
        ├── api-design.md       # API 設計規範
        ├── config-security.md  # 配置管理、安全實踐
        ├── database.md         # 資料庫設計、Migration
        ├── performance.md      # 效能考量
        ├── git.md              # Git 工作流、Commit 格式
        ├── testing.md          # TDD 規範、覆蓋率要求
        └── workflow.md         # 工具選型、綠地/褐地開發流程
```

---

## 快速開始

### 1. 查看簡報

用瀏覽器開啟 `presentation.html`，了解整體 AI 工作流策略。

### 2. 套用 AI 代理憲章

將 `CLAUDE.md` 複製到你的專案根目錄，並依照專案情況填入：

```
Project: [你的專案名稱]
Description: [專案描述]
Tech Stack: [Java 21 / Spring Boot 3.x / ...]
```

### 3. 安裝規範文件

將 `.claude/rules/` 目錄複製到你的專案 `.claude/rules/`，Claude Code 會自動載入所有規則。

### 4. 安裝 Custom Commands

```bash
cp commands/verify.md ~/.claude/commands/
cp commands/learn.md ~/.claude/commands/
```

安裝後在 Claude Code 中即可使用：
- `/verify` — 執行完整驗證（編譯 → 測試 → 覆蓋率）
- `/learn` — 提取本次 session 的知識，評分後存入記憶

### 5. 安裝 Skills

將 `skills/` 下需要的 skill 目錄複製到 `~/.claude/skills/`：

```bash
# 複製單一 skill（以 tdd-workflow 為例）
cp -r skills/tdd-workflow ~/.claude/skills/

# 或複製全部
cp -r skills/* ~/.claude/skills/
```

### 6. 設定 MCP 伺服器

參考 `mcp-guide.md`，安裝建議的 MCP 伺服器（Context7、GitHub、Chrome DevTools 等）。

---

## 相關資源

- [Claude Code 官方文件](https://docs.anthropic.com/claude-code)
- [MCP 伺服器市集](https://www.npmjs.com/search?q=mcp-server)
- [OpenSpec](https://github.com/Fission-AI/OpenSpec)
- [Superpowers](https://github.com/obra/superpowers)
- `mcp-guide.md` — 本倉庫 MCP 安裝指南
