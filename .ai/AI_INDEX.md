# AI Index / AI 目錄與索引

This is the root index for all AI guidelines, rules, and prompts in this project.
這是本專案所有 AI 指南、規則與提示詞的根目錄索引。

## Directory Structure / 目錄結構

- `AI_INDEX.md`: Current file. The structural index and entry point for AI rules. (目前的檔案。AI 規則的結構索引與入口點。)
- `GENERAL_RULES.md`: Universal rules, language settings, and high-level architecture. (通用規則、語言設定與高層次架構。)
- `SECURITY_RULES.md`: Code and data security guidelines, prioritizing security over performance. (程式碼與資料安全規範，強調安全優先於效能。)
- `TESTING_GUIDELINES.md`: Testing strategies, standards, and best practices. (測試策略、標準與最佳實踐。)
- `VCS_GUIDELINES.md`: Version control workflow, branching model, and commit standards. (版本控制工作流程、分支模型與提交標準。)
- `PROJECT_SPECIFIC.md`: Project-specific context, persona, tech stack, and other custom rules. (專案特定的上下文、角色設定、技術棧與其他客製化規則。)
- `PROMPTS.md`: Prompt templates for starting conversations or tasks in different IDEs/AI tools. (供不同 IDE/AI 工具中啟動對話或任務的提示詞模板。)

## Reading Order / 讀取順序

For AI tools to properly understand the project context, follow this reading order:
為了讓 AI 工具正確理解專案上下文，判斷邏輯時請遵循以下讀取順序：
1. `AI_INDEX.md` (To understand structure / 理解結構與維護規範)
2. `GENERAL_RULES.md` (To understand universal rules & constraints / 理解通用規則與限制)
3. `SECURITY_RULES.md` (To understand security priorities / 理解安全優先事項)
4. `TESTING_GUIDELINES.md` (To understand testing standards / 理解測試標準)
5. `VCS_GUIDELINES.md` (To understand version control standards / 理解版本控制標準)
6. `PROJECT_SPECIFIC.md` (To understand project-specific context / 理解專案特定上下文)

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
