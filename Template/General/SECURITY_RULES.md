# Security Rules / 安全規則

這份文件定義了專案開發中必須遵守的程式碼與資料安全規範。所有開發活動都應將安全性視為最高優先級，其重要性高於功能實作速度與系統效能。

## 1. Core Principle / 核心原則

- **安全優先 (Security First)**: 在設計、開發、審查程式碼時，必須優先考慮安全性。當安全性與效能或便利性衝突時，應優先選擇更安全的方案。
- **縱深防禦 (Defense in Depth)**: 不應依賴單一安全措施。應在系統的不同層級（前端、後端、資料庫、基礎設施）建立多層次的安全防護。

## 2. Data Security / 資料安全規範

- **禁止硬編碼敏感資訊 (No Hardcoded Secrets)**:
  - 嚴禁在程式碼中直接寫入任何 API 金鑰、密碼、資料庫連線字串、Token 等敏感資訊。
  - **必須** 使用環境變數 (Environment Variables) 或專門的密鑰管理服務 (如 Vault, AWS Secrets Manager) 來管理。

- **輸入驗證與清理 (Input Validation & Sanitization)**:
  - **絕對不要** 信任任何來自客戶端的輸入。
  - 所有外部輸入（包括 URL 參數、POST body、Headers）都必須經過嚴格的驗證與清理，以防止 SQL Injection, XSS, Command Injection 等攻擊。

- **避免記錄敏感資料 (Avoid Logging Sensitive Data)**:
  - 嚴禁在 Log 中記錄個人身份資訊 (PII)、密碼、信用卡號、Token 等敏感內容。
  - 在記錄前，應對可能包含敏感資訊的欄位進行遮蔽 (Masking) 或移除。

- **安全傳輸 (Secure Transmission)**:
  - 所有對外通訊 **必須** 使用 TLS/SSL (即 HTTPS) 進行加密。

## 3. Code Security / 程式碼安全規範

- **最小權限原則 (Principle of Least Privilege)**:
  - 程式或服務的執行身份應只具備其完成任務所需的最小權限。
  - 資料庫使用者、API 金鑰等應根據其用途被授予嚴格限制的權限。

- **安全的錯誤處理 (Secure Error Handling)**:
  - 嚴禁將詳細的錯誤訊息、堆疊追蹤 (Stack Traces) 或內部系統細節直接回傳給終端使用者。
  - 應使用統一的、模糊的錯誤訊息，並在伺服器端記錄詳細的錯誤日誌以供除錯。

- **依賴項管理 (Dependency Management)**:
  - 定期掃描專案的依賴項，檢查是否存在已知的安全漏洞 (Vulnerabilities)。
  - 保持依賴項更新至安全的版本。

- **伺服器端驗證 (Server-Side Validation)**:
  - 即使前端已進行驗證，後端 **必須** 再次執行完整的資料驗證，將前端驗證視為提升使用者體驗的輔助手段，而非安全屏障。