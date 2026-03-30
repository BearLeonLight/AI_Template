# AI Index / AI 目錄與索引

This is the root index for all AI guidelines in this project. It establishes a three-tier structure: **Project Overview**, **General Rules**, and **Project Guide**.
這是本專案所有 AI 指南的根目錄索引。它建立了一個三層結構：**專案概覽**、**通用規則**與**專案引導**。

## Reading Order & Logic / 讀取順序與邏輯

For AI tools to properly understand the project context, follow this reading order:
為了讓 AI 工具正確理解專案上下文，判斷邏輯時請遵循以下讀取順序：

### Part 0: Project Overview (Highest Level) / 第零部分：專案概覽 (最高層級)
This file provides the overall context of the repository.
此檔案提供儲存庫的整體上下文。

1.  **`README.md`**: Understand the purpose of this repository, the core concepts, and the overall structure. (理解此儲存庫的用途、核心概念及整體結構。)

### Part 1: General Rules (Universal) / 第一部分：通用規則 (適用於所有專案)

These files are located in the `.ai/General/` directory. They provide the foundational, non-negotiable principles for development.
這些檔案位於 `.ai/General/` 目錄中，提供了基礎的、不可協商的開發原則。

1.  **`.ai/General/GENERAL_RULES.md`**: Understand universal rules, language settings, and high-level architecture. (理解通用規則、語言設定與高層次架構。)
2.  **`.ai/General/SECURITY_RULES.md`**: Understand security-first principles and specific security requirements. (理解安全優先原則與具體安全要求。)
3.  **`.ai/General/TESTING_GUIDELINES.md`**: Understand testing strategies and quality standards. (理解測試策略與品質標準。)
4.  **`.ai/General/VCS_GUIDELINES.md`**: Understand the version control workflow and commit standards. (理解版本控制工作流程與提交標準。)
5.  **`.ai/General/PROMPTS.md`**: Find templates for system instructions and specific tasks. (查找系統指令與特定任務的提示詞模板。)

### Part 2: Project Guide (Override) / 第二部分：專案引導 (覆寫通用規則)

This file is located in the `.ai/` root directory. Its rules **override** or **extend** the general rules.
此檔案位於 `.ai/` 根目錄。它的規則會**覆寫**或**擴展**通用規則。

1.  **`.ai/PROJECT_GUIDE.md`**: Understand the project's directory structure, tech stack, API conventions, coding standards, and other specific contexts. (理解專案的目錄結構、技術棧、API 慣例、編碼標準與其他特定上下文。)

---

### ⚠️ CRITICAL INSTRUCTION FOR AI / 給 AI 的關鍵指令

When a project-specific rule conflicts with a general rule, the **project guide always takes precedence**. Your primary role is to adhere to the unique requirements of this project.
當專案引導規則與通用規則衝突時，**永遠以專案引導規則為準**。您的首要職責是遵守此專案的獨特要求。
