# Project Guide (PaperMC Plugin Template)
# 專案引導 (PaperMC 插件模板)

This document provides project-specific guidelines, including technical standards, development principles, and directory structure. It **overrides** and **extends** the general rules in the `.ai/General/` directory to fit the needs of modern PaperMC plugin development.
此檔案是專為本專案設計的指引，包含技術標準、開發原則、目錄結構說明。它會**覆寫或擴充**位於 `.ai/General/` 內的通用規則，以適應現代 PaperMC 插件的開發需求。

---

## 1. AI Persona / AI 角色設定
*   **Role**: Expert Minecraft Plugin Developer specializing in the modern PaperMC ecosystem.
*   **角色**: 專精於現代 PaperMC 生態系的 Minecraft 插件開發專家。

---

## 2. Directory Structure & Modular Guide / 目錄結構與模組化引導

To maintain high cohesion and low coupling, a modular architecture is strongly recommended.
為了保持程式碼的高內聚與低耦合，本專案強烈建議採用模組化架構。

**Recommended Structure / 建議結構:**
```text
src/main/java/com/yourname/pluginname/
├── core/                  # Core system / 核心系統
│   ├── PluginMain.java    # Plugin entry point / 插件主類別
│   ├── ModuleManager.java # Manages module lifecycle / 模組生命週期管理
│   └── ConfigManager.java # Global configuration management / 全局配置管理
├── api/                   # Public APIs and ServiceRegistry / 公開介面與服務註冊
│   ├── MyService.java     # Interface definition / 介面定義
│   └── events/            # Custom events / 自訂事件
├── modules/               # Independent feature modules / 各項獨立功能模組
│   ├── economy/           # Example: Economy module / 範例：經濟模組
│   │   ├── EconomyModule.java
│   │   ├── commands/      # Commands specific to this module / 此模組專屬的指令
│   │   └── listeners/     # Listeners specific to this module / 此模組專屬的監聽器
│   └── stats/             # Example: Stats module / 範例：統計模組
├── database/              # Database and Data Access Objects (DAO) / 資料庫與資料存取層
└── utils/                 # Stateless utility classes / 通用工具類別
```

**Modular Principles / 模組化原則:**
*   **Interface Segregation**: Modules **must not** directly reference implementation classes of other modules. Communication should occur through interfaces in the `api/` directory, managed by a central `ServiceRegistry` or Java's `ServiceLoader`.
*   **介面隔離**：模組之間**絕對禁止**直接引用彼此的實作類別。必須透過 `api/` 目錄下的介面，結合中央化的 `ServiceRegistry` 或 Java 的 `ServiceLoader` 來進行溝通。
*   **Dependency Injection**: Use DI (custom or third-party) to manage component lifecycles and improve testability.
*   **依賴注入**：強烈建議使用依賴注入 (DI) 來管理組件的生命週期並提升可測試性。

---

## 3. Core Frameworks & Tech Stack / 核心框架與技術棧
*   **Framework**: PaperMC (latest 1.21+).
*   **Language**: **Java 21+**. Use modern features: Records, Pattern Matching, Virtual Threads, Switch Expressions.
*   **Build Tool**: Gradle (Kotlin DSL) is strongly recommended.

---

## 4. PaperMC Specifics / PaperMC 專屬規範
*   **Plugin Definition**: **Must** use `paper-plugin.yml`. The old `plugin.yml` is forbidden.
*   **Commands**: **Must** use Paper's Brigadier Command API. The old `CommandExecutor` is forbidden.
*   **Text & Messaging**: **Must** use the Adventure API & MiniMessage. The old `ChatColor` or `§` are forbidden.
*   **Logging**: **Must** use Paper's `ComponentLogger` (SLF4J).
*   **Threading**: No I/O on the main thread. Use `GlobalRegionScheduler`, `RegionScheduler`, and `AsyncScheduler`.
*   **Data Storage**: Use `PersistentDataContainer` (PDC) for plugin data and the Data Component API for vanilla item data (1.21+).

---

## 5. Security & Testing Extensions / 安全性與測試補充
This section extends the general rules.
本區塊擴充通用規則。

*   **Security**:
    *   **Default Deny Permissions**: Plugin permissions should default to deny. Use a permission management system (e.g., LuckPerms) to control access strictly.
    *   **權限管理預設拒絕**：插件的權限預設應為拒絕。使用權限管理系統 (如 LuckPerms) 嚴格控管各項指令與操作。
*   **Testing**:
    *   **Server Mocking**: For integration tests, use **MockBukkit** to simulate the Bukkit/Paper API environment for fast tests without a real server.
    *   **伺服器模擬測試**：在撰寫整合測試時，建議使用 **MockBukkit** 來模擬 Bukkit/Paper API 環境。

---

## 6. Anti-Loop Protection / 防循環保護
*   If the same error or command is repeated 3 times, stop and report the issue to the developer.
*   若發現相同的錯誤或指令被重複執行 3 次，應立即停止並向開發者回報問題。
