# 工作流規範（Workflow Guidelines）

## 工具選型原則

| 工具 | 優勢 | 適用時機 |
|---|---|---|
| **Superpowers brainstorming** | 設計探索、逐步釐清需求、架構選型 | 任何需要設計決策的任務 |
| **tdd-workflow + Superpowers TDD** | 測試規範 + Red-Green-Refactor 紀律 | 所有功能實作與 bug fix |
| **Superpowers writing-plans** | 詳細執行計畫、冷啟動友善 | 綠地開發、需跨 session 執行 |
| **OpenSpec** | 輕量、token 友善、spec 生命週期追蹤 | 褐地開發、spec 變更管理 |

---

## 綠地開發規則（Greenfield）

從零開始的新功能或新專案，使用 **Superpowers 全套流程**：

```
brainstorming
  → writing-plans
    → using-git-worktrees
      → test-driven-development + executing-plans
        → verification-before-completion
          → requesting-code-review
            → finishing-a-development-branch
```

**重點**：設計自由度高，`brainstorming` 階段可大膽探索架構選型，不受既有程式碼約束。`writing-plans` 產出詳細計畫，確保跨 session 執行一致性。

---

## 褐地開發規則（Brownfield）

修改既有系統時，使用 **Superpowers brainstorming + OpenSpec + TDD 紀律**：

```
[影響分析] 列出受影響的檔案、模組、下游依賴
  → brainstorming（設計須考慮既有架構約束）
    → opsx:propose（建立 change：proposal + design + specs + tasks）
      → [選擇性] writing-plans 展開 tasks.md 中的複雜任務（見下方說明）
        → opsx:apply + test-driven-development（每個 task 先測試再實作）
          → verification-before-completion（必須包含回歸測試）
            → opsx:archive（歸檔並同步 delta specs）
```

### 複雜任務展開（選擇性）

tasks.md 的任務粒度為高階（如「實作 XxxService」），遇到以下情況時可對單一任務使用 `writing-plans` 展開：

- 任務涉及多個檔案的連動修改
- 實作模式尚未在 codebase 中建立
- 需要跨 session 執行且不希望重新讀程式碼

`writing-plans` 的產出僅針對該任務，不需要對整個 change 規劃。

### 與綠地的關鍵差異

- 以 `brainstorming` 取代 `opsx:explore`：輕量設計討論，決策記錄在 `design.md`
- 以 `OpenSpec` 取代 `writing-plans`（全域）：tasks.md 追蹤進度，specs 管理規格生命週期
- `writing-plans` 降級為**局部工具**：僅在複雜任務需要時使用，不強制整個 change 都走
- `test-driven-development` 遇到不可測的 legacy code 時，先重構解耦，再補測試，再實作
- `systematic-debugging` 使用頻率高於綠地，優先使用
- `receiving-code-review` 特別重要：審查意見若與既有模式衝突，須先確認再實作
