# AI Index / AI 目錄與索引 (PaperMC 插件通用模板)

This is the root index for all AI guidelines, rules, and prompts in this project.
這是本專案所有 AI 指南、規則與提示詞的根目錄索引。

此為 **現代 PaperMC (1.21+) 插件開發** 的通用 AI 規則模板。

## Directory Structure / 目錄結構

- `AI_INDEX.md`: Current file. The structural index and entry point for AI rules. (目前的檔案。AI 規則的結構索引與入口點。)
- `GENERAL_RULES.md`: Universal rules, language settings, AI persona, and high-level architecture. (通用規則、語言設定、AI 角色設定與高層次架構。)
- `SECURITY_RULES.md`: Code and data security guidelines, prioritizing security over performance. (程式碼與資料安全規範，強調安全優先於效能。)
- `TESTING_GUIDELINES.md`: Testing strategies, standards, and best practices. (測試策略、標準與最佳實踐。)
- `VCS_GUIDELINES.md`: Version control workflow, branching model, and commit standards. (版本控制工作流程、分支模型與提交標準。)
- `PROJECT_SPECIFIC.md`: Tech stack, API guidelines, and core Minecraft/PaperMC rules. (專案技術棧、API 規範與核心 Minecraft/PaperMC 規則。)
- `PROMPTS.md`: Prompt templates for starting conversations or tasks in different IDEs/AI tools. (供不同 IDE/AI 工具中啟動對話或任務的提示詞模板。)
- `PLACEHOLDERS.md`: Documentation of internal MiniMessage placeholders available. (內部 MiniMessage 佔位符文件範例。)

## Reading Order / 讀取順序

For AI tools to properly understand the project context, follow this reading order:
為了讓 AI 工具正確理解專案上下文，判斷邏輯時請遵循以下讀取順序：
1. `AI_INDEX.md` (To understand structure / 理解結構與維護規範)
2. `GENERAL_RULES.md` (To understand universal rules, constraints, and architecture / 理解通用規則、限制與架構)
3. `SECURITY_RULES.md` (To understand security priorities / 理解安全優先事項)
4. `PROJECT_SPECIFIC.md` (To understand tech stack and PaperMC context / 理解技術棧與 PaperMC 開發上下文)
5. `TESTING_GUIDELINES.md` (To understand testing standards / 理解測試標準)
6. `VCS_GUIDELINES.md` (To understand version control standards / 理解版本控制標準)

## Maintenance Rules / 維護規則

### ⚠️ CRITICAL INSTRUCTION FOR AI / 給 AI 的關鍵指令

If you (the AI) are asked to create a new rule file, prompt template, or documentation within the `.ai/` directory, you **MUST** update this `AI_INDEX.md` file immediately.
如果您 (AI) 被要求在 `.ai/` 目錄中建立新的規則檔案、提示詞模板或文件，您 **必須** 立即更新此 `AI_INDEX.md` 檔案。

**Update Procedure / 更新程序**:
1.  Add the new file name to the "Directory Structure" section above.
2.  Provide a brief description of its purpose in both English and Traditional Chinese.
3.  Ensure the structure remains clean and readable.

**更新程序**:
1.  將新檔案名稱新增至上方的「目錄結構」區段。
2.  提供其中英文雙語的簡短用途說明。
3.  確保結構保持整潔與可讀性。

**Anti-Loop Protection / 防循環保護**:
If the exact same error, command, or correction is repeated consecutively (3 times unresolved), immediately stop the current operation and break any infinite loops (including infinite checking, fixing, generating, updating, optimizing, or any AI-related actions). Report the blocking issue and possible causes to the developer proactively, waiting for further instructions.
若發現相同的錯誤、指令或修正動作被重複執行 (連續嘗試 3 次仍未解決時)，應立即停止當前操作，中斷任何無限迴圈 (包含無限檢查、修正、新增、更新、優化等與 AI 相關之動作)，並主動向開發者回報卡住的問題點及可能原因，等待開發者指示。