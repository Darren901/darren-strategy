從這次 session 中提取值得保留的知識，評估品質後存入記憶或升級成 Skill。

## Step 1：提取洞察

回顧這次對話，識別以下類型的洞察：

- **錯誤解法**：解決了什麼問題？根本原因是什麼？如何修復？
- **除錯技巧**：非顯而易見的診斷步驟、有效的工具組合
- **Workaround**：函式庫限制、API 特殊行為、版本特定解法
- **專案模式**：架構決策、程式碼慣例、整合方式

排除：typo 修正、一次性任務細節、不會重複出現的問題。

## Step 2：品質評分

對每個洞察進行五維評分（1-5 分），**全部 ≥ 3 才儲存**：

| 維度 | 說明 |
|---|---|
| **Specificity** | 有程式碼範例或具體步驟？（1=只有概念，5=有完整範例） |
| **Actionability** | 下次遇到時能直接照做？（1=模糊，5=步驟清晰） |
| **Scope Fit** | 名稱與內容一致，沒有超出範圍？ |
| **Non-redundancy** | 與現有 skills / memory 沒有重複？ |
| **Coverage** | 涵蓋主要情境與邊界條件？ |

## Step 3：決定儲存位置

**問自己：這個 pattern 在其他專案也有用嗎？**

- **YES → 全域** `~/.claude/skills/learned/[pattern-name].md`
- **NO → 專案** `.claude/skills/learned/[pattern-name].md`
- **不確定 → 選全域**（全域移到專案比反方向容易）

## Step 4：確認後再建立

完成評分與位置決定後，**先輸出確認表格，等待使用者核准，才能建立任何檔案**：

```
## 準備儲存以下內容，確認後繼續？

| # | 洞察名稱 | 評分 | 儲存位置 |
|---|---|---|---|
| 1 | redis-distributed-lock-lua | 4.8/5 | ~/.claude/skills/learned/ |
| 2 | db-unique-constraint-retry | 4.6/5 | ~/.claude/skills/learned/ |

請確認（全部 OK / 哪幾個不要 / 全部略過）
```

使用者確認後，只建立被核准的項目。

**禁止在使用者確認前呼叫 Write 工具建立任何 skill 或 memory 檔案。**

若洞察通過品質門檻，建立 Skill 檔案：

```markdown
---
name: [pattern-name]
description: [一句話描述：什麼情況下這個 pattern 有用]
learned_from: [session 日期 / 專案名稱]
---

## 問題

[描述遇到了什麼問題或情境]

## 解法

[步驟或程式碼範例]

```java
// 具體範例
```

## 適用時機

- [條件 1]
- [條件 2]

## 注意事項

- [避坑點或限制]
```

若洞察複雜、需要完整的 Skill 結構（含 Anti-patterns、多個範例等），改用 `writing-skills` skill 協助撰寫。

## Step 5：更新 Memory

讀取 `~/.claude/projects/` 下對應專案的 `memory/MEMORY.md`，確認：
- 有無需要更新的既有記憶？
- 有無需要新增的 key insight？

## Step 6：輸出報告

```
## /learn 學習報告

### 本次 Session 重點
[1-3 句描述]

### 提取結果
| 洞察 | 評分 | 結果 | 儲存位置 |
|---|---|---|---|
| [名稱] | 4.2/5 | ✅ 儲存 | ~/.claude/skills/learned/xxx.md |
| [名稱] | 2.0/5 | ❌ 品質不足，未儲存 | - |

### Memory 更新
- [更新或新增的內容摘要]

### 建議
[若有值得建立完整 Skill 的主題，在此提出]
```
