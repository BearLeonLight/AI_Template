# Internal Placeholders / 內部佔位符 (通用模板範例)

## Overview / 概述
This document serves as an example of how to list internal MiniMessage placeholders available globally within a project's localization system.
此文件作為範例，展示如何列出專案本地化系統中全域可用的內部 MiniMessage 佔位符。

*(此為範例文件，請依據實際專案實作的 `LanguageManager` 或類似系統進行修改)*

## Global Placeholders / 全域佔位符

These placeholders are available in **all** language messages retrieved via the localization system.
這些佔位符在所有透過本地化系統取得的語言訊息中皆可使用。

| Placeholder (Tag) | Description (Description) | Data Source (資料來源) |
| :--- | :--- | :--- |
| `<version>` | The current version of the plugin. <br> 插件目前的版本。 | `plugin.getPluginMeta().getVersion()` |
| `<authors>` | The authors of the plugin. <br> 插件的作者列表。 | `plugin.getPluginMeta().getAuthors()` |
| `<prefix>` | The plugin's standard prefix. <br> 插件的標準前綴。 | `config.yml` -> `prefix` |

## Usage Example / 使用範例

In your language configuration (e.g., `messages.yml`):
```yaml
plugin-info: |
  <prefix> <gradient:#5e4fa2:#f79459>MyAwesomePlugin</gradient> <gray>v<version></gray>
  <gray>Authors: <authors></gray>
```

## Extension Guide / 拓展指南

To add new global placeholders, refer to your project's specific implementation of Adventure's `MiniMessage` builder or your custom Language Manager.
若要新增全域佔位符，請參考專案特定的 Adventure `MiniMessage` 構建器實作或自訂的語言管理器。