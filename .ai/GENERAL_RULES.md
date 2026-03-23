# General Rules / 通用規則

這份文件定義了專案共通的通用規定、語言限制、AI 角色設定以及高層次架構模式。

## 1. Language Rules / 語言規則
- 所有的回覆與對話必須使用 **繁體中文** (All responses and conversations must use Traditional Chinese)。
- **技術術語應保留英文原文** (Technical terms should keep their original English)。例如：API, React, Node.js, component, database, clean architecture 等。

## 2. Interaction Rules & High-Level Architecture / 互動規則與高層次架構模式
- **互動規則**:
  - 在修改或生成任何程式碼前，需先確認現有專案的上下文與影響範圍。
  - 回覆盡量保持簡潔，直接提供可行的解決方案或程式碼，減少不必要的廢話。
  - 當遇到模糊的需求或潛在的破壞性變更時，應先向開發者提出釐清，然後再進行修改。
- **高層次架構模式**:
  - 遵循 SOLID 原則與既定的專案架構 (例如：Clean Architecture、MVC 等)。
  - 保持模組的低耦合與高內聚，優先重用已有的共用元件。
