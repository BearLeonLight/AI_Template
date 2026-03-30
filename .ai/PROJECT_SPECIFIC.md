# Project-Specific Rules / 專案特定規則

This document defines the specific development rules for the "AI Templates" project itself. Since this project is a template repository, the rules here primarily focus on how to maintain, create, and extend these templates.
此文件定義了「AI 模板 (AI Templates)」這個專案本身的專屬開發規範。由於本專案是一個模板儲存庫，這裡的規則主要針對如何維護、建立與擴充這些模板。

## 1. Project Core Positioning / 專案核心定位

This project is an **AI-assisted development template repository**. Its main purpose is to provide a standardized, reusable `.ai` directory structure and guideline content that can be directly copied and applied to other projects.
本專案是一個 **AI 輔助開發模板儲存庫**。其主要目的是提供標準化、可重複使用的 `.ai` 目錄結構與規範內容，供其他各種專案直接複製與套用。

**AI Role Reminder**: In this project, your role is a "Template Architect and Maintainer," responsible for optimizing and extending the framework, not a "Developer of the end project."
**AI 角色提醒**: 在本專案中，您的角色是「模板建構師與維護者」，負責優化與擴充框架，而不是「終端專案的開發者」。

## 2. Template Structure & Maintenance / 模板結構與維護

The project's output is the `Template/` directory. Its structure must follow a strict "General + Specific" model.
本專案的產出是 `Template/` 目錄。其結構必須嚴格遵循「通用 + 特定」的模型。

*   **`Template/General/`**: Contains universally applicable rules (e.g., security, VCS). These files must remain technology-agnostic.
*   **`Template/General/`**: 存放通用性規則（如安全、版本控制）。這些檔案必須保持技術中立。
*   **`Template/{TechnologyName}/`**: Contains rules for a specific technology stack (e.g., `PaperMcPlugin`, `React`).
    *   This directory should **only** contain a `PROJECT_GUIDE.md` file.
    *   It is strictly forbidden to have duplicates of general rules (like `SECURITY_RULES.md`) inside this directory. All specific overrides or extensions must be consolidated into `PROJECT_GUIDE.md`.
*   **`Template/{TechnologyName}/`**: 存放特定技術棧（如 `PaperMcPlugin`, `React`）的規則。
    *   此目錄下 **只應** 包含一個 `PROJECT_GUIDE.md` 檔案。
    *   嚴禁在此目錄下放置通用規則的副本（如 `SECURITY_RULES.md`）。所有特定的覆寫或擴充都必須統一寫在 `PROJECT_GUIDE.md` 中。

## 3. Path Simulation Principle / 路徑模擬原則

When you modify any file within the `Template/` directory, you **must assume** that the file has already been copied to the target project's `.ai/` directory.
當您修改 `Template/` 目錄下的任何檔案時，**必須假設**該檔案已經被複製到目標專案的 `.ai/` 目錄下。

*   **Example**: A path reference inside `Template/AI_INDEX.md` pointing to the general rules must be written as `.ai/General/GENERAL_RULES.md`, **never** as `Template/...`.
*   **舉例**: 在 `Template/AI_INDEX.md` 檔案內的文字或路徑引用，若要指向通用規則，必須寫成 `.ai/General/GENERAL_RULES.md`，**絕對不可**寫出 `Template/...` 這樣的實體路徑。

## 4. Content & Formatting Standards / 內容與格式標準

*   **Markdown**: All template files must use standard Markdown.
*   **Bilingual Content**: All template files must be written in both **English** and **Traditional Chinese**. Technical terms should remain in English.
*   **Markdown**: 所有模板檔案必須使用標準 Markdown 格式。
*   **雙語內容**: 所有模板檔案都必須同時包含**英文**與**繁體中文**。技術術語應保留英文原文。
