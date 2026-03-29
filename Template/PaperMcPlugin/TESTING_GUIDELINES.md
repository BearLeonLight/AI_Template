# Testing Guidelines / 測試規範 (PaperMC 插件通用模板)

此文件定義了專案的測試策略、標準與最佳實踐，旨在確保程式碼的品質、穩定性與可維護性。

## 1. Core Philosophy / 核心理念
- **測試金字塔 (Testing Pyramid)**: 我們的測試策略基於測試金字塔模型。我們強調撰寫大量的單元測試，輔以適量的整合測試，並僅在關鍵業務流程上實作少量端對端測試。
- **品質內建 (Quality Built-in)**: 測試不僅是為了找出 bug，更是為了確保程式碼設計的合理性與可維護性。開發者在撰寫功能的同時，就有責任為其撰寫對應的測試。

## 2. Types of Tests / 測試類型
- **單元測試 (Unit Tests)**:
  - **目的**: 驗證單一函式、類別或模組的行為是否符合預期。
  - **要求**: 必須快速、獨立且不依賴外部環境（如真實伺服器、資料庫）。應使用 Mock 或 Stub 來隔離依賴。
- **整合測試 (Integration Tests)**:
  - **目的**: 驗證多個模組協同工作時的正確性，例如服務層與資料存取層的互動。
  - **要求**: 可連接至測試專用的資料庫或模擬伺服器環境。
- **端對端測試 (End-to-End Tests)**:
  - **目的**: 模擬真實玩家操作，驗證完整的業務流程是否正常。
  - **要求**: 僅用於最關鍵的核心流程，例如玩家登入邏輯、核心指令觸發等。

## 3. Frameworks & Tools / 框架與工具 (推薦)
- **Unit/Integration Testing Framework**: JUnit 5
- **Mocking Library**: Mockito
- **Server Mocking**: MockBukkit (用於模擬 Bukkit/Paper API 環境，執行不需要真實伺服器的快速測試)
- **Database Testing**: Testcontainers (用於啟動臨時的 Docker 資料庫進行整合測試)

## 4. Quality Standards / 品質標準
- **測試覆蓋率 (Test Coverage)**: 專案的目標測試覆蓋率應大於 **70%**。核心業務邏輯應達到更高。
- **測試命名**: 測試案例的名稱應清晰描述其測試的行為，例如 `shouldReturnTrueWhenPlayerHasPermission` 或 `testPlayerJoinInitialization`。

## 5. Mocking & Stubbing / 模擬與樁數據
- **原則**: 當被測單元依賴外部模組（如 API 呼叫、資料庫查詢）或 Bukkit/Paper API 時，應使用 Mock (如 Mockito) 來模擬這些依賴的行為。
- **目標**: 確保單元測試的獨立性與確定性，避免因外部服務或伺服器環境的缺失而導致測試失敗。
- **警告**: 不要過度 Mock 內部邏輯，否則測試會失去意義。應測試「行為」而非「實作細節」。