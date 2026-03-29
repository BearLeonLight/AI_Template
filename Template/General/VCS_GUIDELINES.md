# Version Control System (VCS) Guidelines / 版本控制規範

此文件定義了專案的版本控制工作流程、分支模型與提交訊息標準，以確保協作效率與版本歷史的清晰度。

## 1. Branching Model / 分支模型

本專案採用 **GitFlow** 作為核心分支策略，主要分支如下：
- **`main` (或 `master`)**: 用於存放穩定、可隨時發布的正式版本。只接受來自 `develop` 分支的合併。
- **`develop`**: 開發主分支，整合所有已完成的功能。此分支應保持相對穩定，是新功能分支的基礎。
- **`feature/<feature-name>`**: 用於開發新功能的分支。
  - 命名規則: `feature/` 前綴，後面跟隨簡短且描述性的功能名稱（例如 `feature/user-authentication`）。
  - 從 `develop` 分支出來，完成後合併回 `develop`。
- **`hotfix/<issue-name>`**: 用於修復 `main` 分支上的緊急 Bug。
  - 從 `main` 分支出來，完成後必須同時合併回 `main` 和 `develop`。

## 2. Commit Message Format / 提交訊息格式

所有提交訊息都 **必須** 遵循 **Conventional Commits** 規範。此格式有助於自動化版本管理與變更日誌生成。

**格式**: `<type>(<scope>): <subject>`

- **`<type>`**: 提交類型，必須是以下之一：
  - `feat`: 新增功能 (A new feature)
  - `fix`: 修復 Bug (A bug fix)
  - `docs`: 只修改文件 (Documentation only changes)
  - `style`: 不影響程式碼邏輯的格式變更 (e.g., white-space, formatting)
  - `refactor`: 重構程式碼，既非新增功能也非修復 Bug
  - `perf`: 提升效能的程式碼變更
  - `test`: 新增或修改測試
  - `chore`: 維護性工作，如更新建置腳本、套件等
- **`<scope>` (可選)**: 影響範圍，例如模組名稱 (e.g., `auth`, `payment`)。
- **`<subject>`**: 簡潔描述，使用祈使句，首字母小寫，結尾不加句號。

**範例**:
- `feat(auth): add password reset functionality`
- `fix(api): correct user data serialization issue`
- `docs(readme): update setup instructions`
- `refactor(core): simplify internal logic of the main service`

## 3. Pull Request (PR) / Merge Request (MR) Guidelines / 合併請求規範

- **標題**: PR 的標題應清晰、簡潔，並遵循 Commit Message 的格式。
- **描述**:
  - **What**: 這個 PR 做了什麼？
  - **Why**: 為什麼需要這個變更？（例如：修復哪個 Bug、實現哪個需求）
  - **How**: 如何實作的？（可選，若邏輯複雜）
  - **Related Issue**: 關聯的 Issue 編號（例如：`Closes #123`）。
- **審查**: 在合併前，至少需要一位團隊成員的審查批准 (Review Approve)。
- **CI/CD**: 必須等待所有自動化檢查（CI/CD Pipeline）通過後，方可合併。