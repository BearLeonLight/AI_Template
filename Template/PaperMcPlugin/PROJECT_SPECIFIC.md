# 現代 PaperMC 技術棧與規則 (通用模板)

此檔案包含開發現代 PaperMC Plugin 的嚴格技術標準。

## 1. 核心框架 (Core Frameworks)
*   **框架**: [PaperMC](https://papermc.io/) (最新 1.21+)。
*   **語言**: **Java 21+**。
    *   使用現代特性：Records, Pattern Matching, Virtual Threads, Switch Expressions。
*   **構建工具 (Build Tool)**: 強烈建議使用 Gradle (Kotlin DSL)。
    *   若絕對需要 NMS，請使用 `io.papermc.paperweight.userdev` 進行 NMS/Mojang Mappings。
    *   使用 `xyz.jpenilla.run-paper` 進行本地測試。

## 2. 配置管理 (Configuration)
*   **函式庫**: 建議使用 Configurate (SpongePowered)。極不建議使用舊版的 Bukkit `FileConfiguration` (`config.yml` API)。
*   **實踐**: **必須** 使用 **物件映射 (Object Mapping)**。定義 `record` 或帶有 `@ConfigSerializable` 註解的類別來映射設定檔。避免直接呼叫 `getNode("path").getString()` 等取值方法。

## 3. PaperMC 規範 (PaperMC Specifics)
*   **插件定義 (Plugin Definition)**:
    *   **必須** 使用 `paper-plugin.yml`。禁止使用傳統的 `plugin.yml`。
*   **API 使用**:
    *   優先使用 PaperMC API，勝於 Bukkit/Spigot API。
    *   **註冊表 (Registry)**: 對於所有遊戲內容（附魔、實體類型、物品等），使用 `RegistryAccess` 與 `NamespacedKey` (`Key`)。若存在註冊表，避免直接使用字串鍵值或 Enum 名稱。
*   **生命週期、指令與事件 (Lifecycle, Commands & Events)**:
    *   **指令**: **必須** 使用 PaperMC 的 **Brigadier Command API** (透過 `LifecycleEvents.COMMANDS`)。禁止使用舊版 `CommandExecutor`。
    *   **事件**: 使用 Paper 的現代化、精確的事件註冊方式。
        *   **推薦**: `server.getPluginManager().registerEvent(PlayerJoinEvent.class, listener, EventPriority.NORMAL, (l, e) -> handleJoin((PlayerJoinEvent) e), this)`
        *   **不建議**: `server.getPluginManager().registerEvents(this, this)`
*   **文字與訊息 (Text & Messaging)**:
    *   **必須** 使用 [Adventure API](https://docs.advntr.dev/) 與 `MiniMessage`。禁止使用舊版 `ChatColor` 或 `§`。
*   **日誌 (Logging)**:
    *   **必須** 使用 Paper 提供的 `ComponentLogger` (SLF4J) (`plugin.getComponentLogger()`)。
    *   **上下文 (Context)**: 所有錯誤日誌 **必須** 包含足夠的上下文（例如：玩家 UUID、名稱、座標）以利除錯。

## 4. 並發與資料庫 (Concurrency & Database)
*   **線程原則 (Threading Principle)**: 主線程 (Main Thread) 禁止執行任何 I/O 操作 (網路、檔案、資料庫)。
*   **排程器 API (相容 Folia)**: 使用 `GlobalRegionScheduler`, `RegionScheduler`, 和 `AsyncScheduler`。不建議使用舊版 `Bukkit.getScheduler()`。
*   **虛擬執行緒 (Virtual Threads)**: 用於高吞吐量、非伺服器 API 的任務。**警告：絕對禁止在虛擬執行緒內呼叫 Bukkit/Paper API。**
*   **資料庫**:
    *   **連接池 (Connection Pooling)**: **必須** 使用如 **HikariCP** 等連接池進行關聯式資料庫連接。
    *   **非同步操作**: 所有資料庫查詢必須使用 `AsyncScheduler` 和 `CompletableFuture` 進行非同步執行。

## 5. 數據結構與存儲 (Data Structures & Storage)
*   **玩家資料快取 (Player Data Cache)**:
    *   **線上玩家**: 使用 `Map<UUID, PlayerData>`。若有非同步線程存取，**必須** 使用 `ConcurrentHashMap`。
    *   **離線玩家**: 考慮使用帶有驅逐策略的快取 (Eviction Policy)（例如 Caffeine, Guava Cache）以防止 Memory Leaks。
*   **物品/實體數據 (Item/Entity Data)**:
    *   **插件數據**: 使用 `PersistentDataContainer` (PDC)。
    *   **原版物品數據 (1.21+)**: **必須** 使用 Paper 的 **Data Component API** (`item.getData(DataComponentTypes.XXX)`)。極不建議使用舊版的 `ItemMeta` 方法。

## 6. Java 最佳實踐 (Java Best Practices)
*   **語法**: 使用 `var`、`record` 與不可變集合 (`List.of()`, `Map.copyOf()`)。
*   **空值安全 (Null Safety)**: 使用 `@NotNull`、`@Nullable` 與 `Optional<T>`。

## 7. 防循環保護 (Anti-Loop Protection)
*   若發現相同的錯誤、指令或修正動作被重複執行 (連續嘗試 3 次仍未解決時)，應立即停止當前操作，中斷任何無限迴圈 (包含無限檢查、修正、新增、更新、優化等與 AI 相關之動作)，並主動向開發者回報卡住的問題點及可能原因，等待開發者指示。