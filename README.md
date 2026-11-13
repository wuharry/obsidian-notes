---
title: 遊戲設計與專案總覽看板
tags:
  - dashboard
  - gamedesign
  - index
updated: 2026-11-13
---

# 🎮 遊戲企劃與開發筆記總覽 (Vault Dashboard)

> [!abstract] **工作區視覺化導航**
> 本庫收錄三大核心專案之即時狀態與規格架構，全面採用視覺化圖表與矩陣呈現。

---

## 🗺️ 專案總覽拓撲圖 (Project Map)

```mermaid
graph TB
    subgraph Hub["🎯 遊戲專案核心矩陣 (2026-11-13)"]
        direction TB
        SW["🚀 Star Warfare<br/><b>雙軌制開發 (Godot TPS)</b>"]
        CG["🃏 紙鴉牌 Deckmarch<br/><b>R25/R26 多端發行 (Godot 4.7)</b>"]
        RPG["🎲 2D-3D TRPG<br/><b>雙軌渲染與引擎硬結算 (Web)</b>"]
    end

    subgraph SW_Tracks["Star Warfare 雙軌架構"]
        SW_Main["🌿 main: 現代化重製 (Mobile-First / HD2)"]
        SW_Classic["🏛️ codex/classic-hd: 1:1 高清復刻版"]
    end

    subgraph CG_Ecosystem["紙鴉牌 生態與管線"]
        CG_Client["📱 多端發布: Windows / Mac (R26) / Android (AAB) / iOS"]
        CG_Sec["🛡️ 安全與對局: TOTP 鑑權 / 同網防刷 / 梯位天梯"]
    end

    subgraph RPG_Pipeline["Web TRPG 執行管線"]
        RPG_Core["⚙️ 規則硬結算: 觸發規則 (Trigger Rules) + 敘事持有物"]
        RPG_Town["🏰 城鎮雙軌: HD-2D 等角 3D / 純 2D 像素降級"]
    end

    SW --> SW_Tracks
    CG --> CG_Ecosystem
    RPG --> RPG_Pipeline
```

---

## 📊 三大專案狀態矩陣 (Status Matrix)

| 專案名稱 | 最新版本 | 核心引擎 / 平台 | 當前里程碑 | 關鍵進展與驗證焦點 | 詳情連結 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **🚀 Star Warfare** | `v0.7` (雙軌定案) | Godot 4.x (Angle/Compat) | 雙軌分支分割完成 | `main` 現代重製 vs `classic-hd` 1:1 復刻；裝甲流水線與工蟲 AI 落地 | [[Notion/🎮StarWarfare企劃\|專案詳情]] |
| **🃏 紙鴉牌 Deckmarch** | `R26` (Client) / `R25` (Server) | Godot 4.7.2 Forward+ / Multi | 多平台商用驗收 | Android AAB 包、iOS 原生 Keychain、TOTP 管理鑑權、同網防刷 | [[Notion/HD-2D 卡牌對戰 (暫定) - 遊戲設計文件 v2.0\|專案詳情]] |
| **🎲 2D-3D RPG / TRPG** | `v2.4` (24 場實測) | trpg-server + WebGL/Canvas | 第二章直開 + 觸發結算 | 主線線索引擎硬結算、敘事持有物、結構化回合紀錄、HD-2D 城鎮雙軌 | [[Notion/專案名稱：(待定) 2D-3D 動作 RPG 企劃案\|專案詳情]] |

---

## 🚀 1. Star Warfare：雙軌開發架構

```mermaid
flowchart LR
    A[Star Warfare 專案倉庫] --> B{開發主線分軌 2026-11-12}
    
    B -->|現代優化主線| C["🌿 main (Remake Track)"]
    C --> C1["📱 手機優先 + PC 輔助"]
    C --> C2["🎯 參考 Helldivers 2 / Warfare 射擊節奏"]
    C --> C3["🎨 Viper 現代獨立重製 + 純色面罩"]
    C --> C4["⚡ 自動武器射速 +30% 與腰射擴散"]

    B -->|忠實復刻主線| D["🏛️ codex/classic-hd (Classic Track)"]
    D --> D1["🔒 嚴格 1:1 原版玩法與數值"]
    D --> D2["🖼️ 高清貼圖與場景修復 (無改版數值)"]
    D --> D3["🧪 逐項核對原版彈藥/計時/掉落"]

    B -->|歷史成果存檔| E["📦 封存標籤 (archive/pre-split-*)"]
```

---

## 🃏 2. 紙鴉牌 (Deckmarch)：商用發布與安全架構

```mermaid
flowchart TD
    subgraph Multiplatform["🌐 多端發行矩陣 (R25 / R26)"]
        direction LR
        Win["🪟 Windows (R26 打包)"]
        Mac["🍏 macOS (R26 Metal)"]
        And["🤖 Android (AAB Gradle)"]
        iOS["🍎 iOS (Keychain 登入)"]
    end

    subgraph Security_FairPlay["🛡️ 商業服務與防作弊防線"]
        TOTP["🔐 管理員 RPC 全面 TOTP 雙因子驗證"]
        AntiCheat["🚫 梯位/天梯 同網段帳號嚴格隔離防刷"]
        Atomic["🗑️ 符合法規之帳號與關聯資料原子刪除"]
        Wallet["💎 測試鑽石申領與審計錢包發放"]
    end

    subgraph Gameplay["⚔️ 核心戰場手感"]
        Board["4路 16格 前後排戰場"]
        Juice["幾何召喚法陣 + Tween 位移衝撞 + Hit Stop"]
        Archetypes["快攻灼燒流 vs 死靈召喚流"]
    end

    Multiplatform --> Security_FairPlay --> Gameplay
```

---

## 🎲 3. Web TRPG / 2D-3D 動作 RPG：引擎硬結算與城鎮管線

```mermaid
sequenceDiagram
    autonumber
    actor Player as 玩家行動
    participant Engine as 規則引擎 (Trigger Rules)
    participant Narrative as 敘事生成 (Narrative Layer)
    participant Memory as 回合日誌與持有物層

    Player->>Engine: 自由文字 / 探索 / 地圖移動
    Engine->>Engine: 觸發規則判定 (非模型主張)
    alt 滿足主線/道具線索
        Engine->>Memory: 寫入「敘事持有物」與世界狀態
        Engine->>Narrative: 派發確定結果標籤 (不可被否定)
    else 出格或無效行為
        Engine->>Narrative: 出格防線攔截 (禁止憑空捏造)
    end
    Narrative-->>Player: 輸出連貫敘事 (回饋一致)
    Memory->>Memory: 留存單回合格局 Log (出 Bug 直接調閱)
```

### 📜 TRPG 實測驗收直達看板

| 場次代號 | 驗收核心 | 成果與狀態 | 跳轉連結 |
| :--- | :--- | :--- | :--- |
| **RUN-024** | 訪客第二章直接開局 | 🟢 驗證通過（跳過第一章重複成本，主線觸發規則鎖定） | [[Notion/專案名稱：(待定) 2D-3D 動作 RPG 企劃案/TRPG測試/README#📜-實測場次索引-session-runs\|📄 查看索引]] |
| **RUN-022** | 密室與場景物件修復 | 🟢 驗收通過（場上物件不再誤判為「你沒有」，密室收束解除） | [[Notion/專案名稱：(待定) 2D-3D 動作 RPG 企劃案/TRPG測試/README#📜-實測場次索引-session-runs\|📄 查看索引]] |
| **RUN-015** | 第一章交劍與持有物 | 🟢 BUG-09 通過（新增敘事持有物層，不看措辭定成敗） | [[Notion/專案名稱：(待定) 2D-3D 動作 RPG 企劃案/TRPG測試/README#📜-實測場次索引-session-runs\|📄 查看索引]] |
| **RUN-001~03**| 酒館啟程與磨坊蜘蛛 | 🟡 早期基準場次（確立出格防線、部位耐傷與擲骰原則） | [[Notion/專案名稱：(待定) 2D-3D 動作 RPG 企劃案/TRPG測試/場次/RUN-001-銀蹄酒館/結果與觀察\|📄 檢視 RUN-001]] |

---

## 💡 Obsidian 專用語法與閱讀提示

> [!tip] **最佳閱讀體驗設定**
> 1. **大綱導航（Outline）**：按 `Ctrl + Shift + E` 或點擊右側欄的大綱圖標，可在長篇文件（如 StarWarfare 企劃或 Bug 表）中瞬間跳轉章節。
> 2. **雙鏈懸停預覽（Page Preview）**：滑鼠移至任意 `[[雙括號連結]]` 上，按住 `Ctrl` 即可在不離開當前頁面的情況下快速預覽目標文檔內容。
> 3. **折疊區塊（Foldable Headings / Callouts）**：文件中標有帶有小箭頭的標題與 Callout 區塊均可點擊折疊收起，減少視覺干擾。
> 4. **標籤面板（Tags）**：可透過右側欄標籤面板快速按 `#trpg`、`#bug-tracker`、`#gamedesign` 進行主題篩選。

