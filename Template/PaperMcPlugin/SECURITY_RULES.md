# Security Rules / 安全規則 (PaperMC 插件通用模板)

這份文件定義了專案開發中必須遵守的程式碼與資料安全規範。所有開發活動都應將安全性視為最高優先級，其重要性高於功能實作速度與系統效能。

## 1. Core Principle / 核心原則

- **安全優先 (Security First)**: 在設計、開發、審查程式碼時，必須優先考慮安全性。當安全性與效能或便利性衝突時，應優先選擇更安全的方案。
- **縱深防禦 (Defense in Depth)**: 不應依賴單一安全措施。應在系統的不同層級（插件層、資料庫層、基礎設施層）建立多層次的安全防護。

## 2. Data Security / 資料安全規範

- **禁止硬編碼敏感資訊 (No Hardcoded Secrets)**:
  - 嚴禁在程式碼中直接寫入任何 API 金鑰、資料庫連線字串、Token 或權限密碼等敏感資訊。
  - **必須** 使用 `config.yml` 或其他配置文件進行管理，並確保這些檔案不會被提交到公開的版本控制庫中（可提供 `.example` 檔案）。

- **輸入驗證與清理 (Input Validation & Sanitization)**:
  - **絕對不要** 信任任何來自客戶端（玩家）的輸入，包含聊天訊息、指令參數、GUI 互動等。
  - 所有外部輸入都必須經過嚴格的驗證與清理，以防止 SQL Injection, Command Injection 或格式化漏洞（如未經過濾的 MiniMessage 標籤）。

- **避免記錄敏感資料 (Avoid Logging Sensitive Data)**:
  - 嚴禁在 Log 中記錄玩家的真實 IP、密碼（若有實作）、或其他 PII (個人身份資訊)。
  - 在記錄前，應對可能包含敏感資訊的欄位進行遮蔽 (Masking) 或移除。

## 3. Code Security / 程式碼安全規範

- **最小權限原則 (Principle of Least Privilege)**:
  - 插件的權限預設應為拒絕（Default Deny）。
  - 使用權限管理系統 (如 LuckPerms) 嚴格控管各項指令、操作和 GUI 互動的權限。只授予完成任務所需的最小權限。
  - 資料庫連線使用的帳號應只具備其操作所需最低權限的表和操作權限。

- **安全的錯誤處理 (Secure Error Handling)**:
  - 嚴禁將詳細的錯誤訊息或堆疊追蹤 (Stack Traces) 直接發送給玩家。
  - 應使用統一的、模糊的錯誤訊息（例如：「發生內部錯誤，請聯絡管理員。」），並在後台 Server Console 記錄詳細的錯誤日誌以供除錯。

- **依賴項管理 (Dependency Management)**:
  - 定期掃描專案的依賴項（如 Gradle 中的依賴），檢查是否存在已知的安全漏洞。
  - 保持依賴項更新至安全的版本。

- **線程安全與並發 (Thread Safety & Concurrency)**:
  - 在多執行緒環境下（特別是 PaperMC 的非同步操作中），確保共享資料的存取是線程安全的，避免 Race Conditions 和 Data Leaks。
  - 嚴禁在非同步線程中直接操作非線程安全的 Bukkit/Paper API，如需操作，請排程回適當的主線程或區域線程（Region Scheduler）。