# AI-Powered Development Templates / AI 驅動開發模板

[![Made with BearLeonLighgt](https://img.shields.io/badge/Made%20with-BearLeonLighgt-blue.svg)](https://github.com/BearLeonLighgt)

This repository serves as a centralized collection of templates for AI-assisted development. It provides a standardized framework (`.ai` directory) to guide AI tools, ensuring consistency, security, and adherence to project-specific standards across different projects.

這個儲存庫是 AI 輔助開發模板的集合，其核心是提供一個標準化的框架 (`.ai` 目錄)，用以引導 AI 工具，確保在不同專案中都能維持一致性、安全性並遵循專案規範。

## Core Concepts / 核心概念

### The `.ai` Directory / `.ai` 目錄

The `.ai` directory is the heart of this framework. It contains a set of markdown files that define the rules, standards, and context for AI tools. By feeding these files to an AI assistant (like GPT, Copilot, etc.), you can train it to understand your project's specific needs.

`.ai` 目錄是此框架的核心。它包含一系列 Markdown 檔案，定義了 AI 工具應遵循的規則、標準與上下文。透過將這些檔案提供給 AI 助理，您可以使其了解專案的特定需求。

### The `Template` Directory / `Template` 目錄

The `Template` directory contains pre-configured `.ai` folder structures for different types of projects. When starting a new project, you can copy the relevant template into your project's root and rename it to `.ai`.

`Template` 目錄包含了針對不同類型專案的預設 `.ai` 結構。當您開始一個新專案時，可以將對應的模板複製到專案根目錄，並將其重新命名為 `.ai`。

**Key Distinction / 關鍵區別:**
- **`Template/`**: Source templates for other projects. (用於其他專案的來源模板。)
- **`.ai/`**: The actual, live configuration for *this* repository. (此儲存庫當前使用的配置。)

## How to Use / 如何使用

1.  **Choose a Template**: Browse the `Template` directory. A typical project setup involves combining `General` and a technology-specific guide.
2.  **Copy and Assemble**:
    *   Create a new `.ai` directory in your project root.
    *   Copy the entire `Template/General/` directory into your new `.ai/` directory.
    *   Copy the `Template/AI_INDEX.md` into your new `.ai/` directory.
    *   From a technology-specific directory (e.g., `Template/PaperMcPlugin/`), copy the `PROJECT_GUIDE.md` into your new `.ai/` directory.
3.  **Customize**: Modify `.ai/PROJECT_GUIDE.md` to match your project's specific needs.
4.  **Integrate with AI**: Use the system prompt from `.ai/General/PROMPTS.md` to instruct your AI assistant to read and follow the rules defined in your `.ai` directory.

## Repository Structure / 儲存庫結構

```
.
├── .ai/                  # AI rules for THIS repository
│   ├── General/          # General, universal rules
│   └── PROJECT_SPECIFIC.md # Specific rules for this repo
├── Template/             # Collection of .ai templates for other projects
│   ├── General/          # Base general rules for all templates
│   ├── PaperMcPlugin/    # Specific template for PaperMC Plugins
│   │   └── PROJECT_GUIDE.md
│   └── AI_INDEX.md       # Generic index for templates
└── README.md             # This file
```

## Contribution / 貢獻

Contributions are welcome! If you have a new template or improvements to existing ones, please follow the guidelines in `.ai/General/VCS_GUIDELINES.md` and submit a Pull Request.
