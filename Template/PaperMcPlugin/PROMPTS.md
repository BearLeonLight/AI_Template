# Prompts / 提示詞模板庫 (PaperMC 插件通用模板)

This file contains **ready-to-use** system instructions or specific task prompts, suitable for guiding AI development assistants like IDEA Gemini Code Assist, Cursor, Copilot, etc.
此檔案存放**實際可用**的系統指令或特定任務提示詞，適用於放置在 IDEA Gemini Code Assist、Cursor、Copilot 等其他 AI 開發輔助軟體的開頭引導。

The purpose of this document is to allow users to easily **copy/paste** these templates to set the behavioral guidelines for the AI assistant.
此文件目的是讓使用者可以方便地**複製/貼上**這些模板，以設定 AI 助手的行為準則。

---

## 1. System Instruction / 系統指令 (全局啟動引導詞)

> **Usage:** Paste this into the "System Prompts" section of your AI tool to ensure the AI reads the guidelines and loads the structured data in every conversation.
> **用途：** 貼在 AI 工具的 System Prompts (系統自訂指令) 區塊，讓 AI 每次對話都能讀取規範並載入結構化資料。

```text
### SYSTEM INSTRUCTION: PROJECT CONTEXT & RULES ###

You are currently working in a modern PaperMC plugin project.
Your behavior MUST be governed by the configuration files located in the `.ai/` directory.

ACTION REQUIRED:
1.  LOCATE and READ the master index file `.ai/AI_INDEX.md` to understand the context structure.
2.  Based on the index, READ `.ai/GENERAL_RULES.md` and `.ai/PROJECT_SPECIFIC.md` for detailed standards.
3.  ADOPT the persona: Expert Minecraft Plugin Developer (Modern PaperMC 1.21+ ecosystem).
4.  APPLY the following critical standards:
    *   **Language**: Traditional Chinese (繁體中文) for all explanations.
    *   **Tech Stack**: Java 21+, PaperMC 1.21+, Gradle/Maven.
    *   **Architecture**: Modular Architecture, low coupling. Use Dependency Injection if applicable.
    *   **API Usage**: Paper API > Bukkit API. Brigadier Commands, Data Components, RegistryAccess.
    *   **Text**: Adventure API (MiniMessage) ONLY. No legacy ChatColor.
    *   **Concurrency**: NO I/O on Main Thread. Use Folia-compatible schedulers or Virtual Threads for pure logic/IO. Use connection pooling (e.g., HikariCP) for DB.
    *   **Documentation**: Bilingual Javadoc (English + Traditional Chinese).

If you cannot access the files directly, you MUST ask the user to provide their content before generating any code.

### END OF INSTRUCTION ###
```

---

## 2. Specific Task Prompts / 特定任務提示詞

> **Usage:** For common development scenarios, users can directly copy these prompts to start a new conversation, ensuring the AI processes the request with the correct context.
> **用途：** 針對常見的開發情境，使用者可以直接複製這些提示詞來開啟新的對話，確保 AI 以正確的上下文進行處理。

### Create New Feature or Module / 建立新功能或模組
```text
我需要建立一個名為 `[FeatureName]` 的新功能。
請遵循 `.ai/GENERAL_RULES.md` 和 `.ai/PROJECT_SPECIFIC.md` 中定義的現代 PaperMC 架構：
1.  建立於正確的套件下 `[BasePackage].[featurename]`。
2.  若有指令，請使用 PaperMC 的 Brigadier Command API。
3.  若有事件監聽，請使用現代的 `registerEvent` 註冊方式，避免反射掃描。
4.  確保主線程上絕對沒有 I/O 操作 (資料庫/檔案)，需要時使用 `AsyncScheduler` 與 `CompletableFuture`。
5.  使用 `MiniMessage` 進行任何訊息傳送。
6.  確保所有 Javadoc 均為雙語（英文/繁體中文）。
```

### Refactor Code / 重構程式碼
```text
請重構選取的程式碼以符合專案的 `.ai/PROJECT_SPECIFIC.md` 規則 (Paper 1.21+ 標準)：
1.  在適當的情況下使用 `var` 與 `record`。
2.  將任何舊版 `ChatColor` 或 `§` 替換為 Adventure API `MiniMessage`。
3.  將舊版的 `ItemMeta` (或 String ID) 操作替換為原版物品數據 `Data Component API` 與 `RegistryAccess`。
4.  確保主執行緒上沒有 I/O 操作，並使用 Folia 相容的排程器。
5.  如果缺少，請新增雙語 Javadoc。
```

### Code Review / 程式碼審查
```text
請根據 `.ai/` 目錄下的所有規則，特別是 `SECURITY_RULES.md` 與 `PROJECT_SPECIFIC.md`，對我即將提供的程式碼進行 Review。
請重點關注：
1. **安全性與併發問題**：是否存在任何違反 `SECURITY_RULES.md` 的問題（如 SQL Injection、未過濾的 MiniMessage），或是 Virtual Thread 中呼叫 Bukkit API 等併發問題。
2. **過時的 API**：是否使用了 Bukkit 舊版 API (如 `plugin.yml`, `CommandExecutor`, `ItemMeta` getters/setters, 字串註冊表, `FileConfiguration`)。
3. **效能與最佳實踐**：潛在的主線程卡頓、資料庫連接池未正確使用，或可以改進的地方。
4. 提供具體可執行的重構建議或現代 PaperMC 的程式碼範例。
```