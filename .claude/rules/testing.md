# 測試規範（Testing Guidelines）

## 強制 TDD 規則

**所有功能實作與 Bug Fix 都必須遵守 TDD 流程，無例外。**

### 兩個 TDD Skill 的分工

| Skill | 用途 |
|---|---|
| `/tdd-workflow` | 測試規範與範例——測試結構、框架用法、覆蓋率配置、常見錯誤 |
| `superpowers:test-driven-development` | Red-Green-Refactor 流程紀律——強制先寫測試、按步驟執行、防止跳過測試直接實作 |

### 執行方式

實作任何功能或修 Bug 時，**必須同時啟動兩者**：

```
/tdd-workflow                         ← 載入測試規範與範例
superpowers:test-driven-development   ← 強制執行 Red-Green-Refactor 紀律
```

兩者互補：`tdd-workflow` 告訴你「怎麼寫測試」，`superpowers:test-driven-development` 確保你「真的先寫測試」。

## 覆蓋率要求

- Line coverage ≥ 80%
- Branch coverage ≥ 80%
- 以 `mvn clean verify` 驗證（JaCoCo check 未達標會 fail build）
