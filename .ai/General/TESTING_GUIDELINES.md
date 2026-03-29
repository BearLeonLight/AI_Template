# Testing Guidelines / 測試規範

此文件定義了專案的測試策略、標準與最佳實踐，旨在確保程式碼的品質、穩定性與可維護性。

## 1. Core Philosophy / 核心理念
- **測試金字塔 (Testing Pyramid)**: 我們的測試策略基於測試金字塔模型。我們強調撰寫大量的單元測試，輔以適量的整合測試，並僅在關鍵業務流程上實作少量端對端測試。
- **品質內建 (Quality Built-in)**: 測試不僅是為了找出 bug，更是為了確保程式碼設計的合理性與可維護性。開發者在撰寫功能的同時，就有責任為其撰寫對應的測試。

## 2. Types of Tests / 測試類型
- **單元測試 (Unit Tests)**:
  - **目的**: 驗證單一函式、類別或模組的行為是否符合預期。
  - **要求**: 必須快速、獨立且不依賴外部環境（如網路、資料庫）。應使用 Mock 或 Stub 來隔離依賴。
- **整合測試 (Integration Tests)**:
  - **目的**: 驗證多個模組協同工作時的正確性，例如服務層與資料存取層的互動。
  - **要求**: 可連接至測試專用的資料庫或外部服務，但應避免依賴生產環境。
- **端對端測試 (End-to-End Tests)**:
  - **目的**: 模擬真實使用者操作，驗證完整的業務流程是否正常。
  - **要求**: 僅用於最關鍵的核心流程，例如使用者註冊、登入、下單等。

## 3. Frameworks & Tools / 框架與工具
> **[TODO: 請根據實際專案填寫]**
> - **Unit/Integration Testing Framework**: (例如：Jest, Vitest, JUnit, PyTest)
> - **E2E Testing Framework**: (例如：Cypress, Playwright, Selenium)
> - **Assertion Library**: (例如：Chai, AssertJ)
> - **Mocking Library**: (例如：Mockito, Sinon.js)

## 4. Quality Standards / 品質標準
> **[TODO: 請根據實際專案填寫或調整]**
> - **測試覆蓋率 (Test Coverage)**: 專案的目標測試覆蓋率為 **80%**。任何新的程式碼都應伴隨測試，以維持或提升整體覆蓋率。
- **測試命名**: 測試案例的名稱應清晰描述其測試的行為，例如 `should return false when password is incorrect`。

## 5. Mocking & Stubbing / 模擬與樁數據
- **原則**: 當被測單元依賴外部模組（如 API 呼叫、資料庫查詢）時，應使用 Mock 或 Stub 來模擬這些依賴的行為。
- **目標**: 確保單元測試的獨立性與確定性，避免因外部服務的不穩定而導致測試失敗。