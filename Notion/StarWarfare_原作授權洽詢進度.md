---
title: Star Warfare 原作資產授權洽詢與版權追蹤
notion-id: sw-license-inquiry-202611
tags:
  - star-warfare
  - license
  - copyright
  - legal
updated: 2026-11-13
---

# ⚖️ Star Warfare 原作資產授權洽詢與進度追蹤

> [!abstract] **授權聯絡總覽 (2026-11-13)**
> 紀錄向原開發商 **Freyr Games** 官方與 Google Play 開發者聯絡人 **尹先生 (Yin)** 針對《Star Warfare: Alien Invasion》美術與音效資產正式商業授權之 4 輪洽詢時序。

---

## 🗺️ 洽詢時序與狀態流程圖

```mermaid
sequenceDiagram
    autonumber
    actor Harvey as 吳浩維 (Harvey)
    participant Freyr as 🏢 Freyr Games 官方信箱<br/>(support@ifreyr.com)
    participant Yin as 👤 尹先生 (開發者窗口)<br/>(yxb98yin@gmail.com)

    Note over Harvey,Freyr: 第一階段：官方窗口洽詢
    Harvey->>Freyr: ✉️ 第 1 輪 (2026-09-25)<br/>資產權利主體確認與商業授權合作意向
    Harvey->>Freyr: ✉️ 第 2 輪 (2026-10-12)<br/>中秋後 Follow-up 追蹤確認是否收到
    Note right of Freyr: ⏳ 官方信箱未回覆

    Note over Harvey,Yin: 第二階段：開發者個人信箱直洽
    Harvey->>Yin: ✉️ 第 3 輪 (2026-10-19)<br/>Google Play 窗口確認，提議提供素材清單
    Harvey->>Yin: ✉️ 第 4 輪 (2026-11-05)<br/>詳述童年情懷、Godot 復原進度，爭取實機演示評估
    Note right of Yin: ⏳ 截至 2026-11-13 尚待回覆
```

---

## 📊 洽詢紀錄明細矩陣

| 輪次 | 發信日期 | 收件對象 | 郵件主旨 | 核心訴求與內容概要 | 目前狀態 |
| :---: | :---: | :--- | :--- | :--- | :---: |
| **01** | `2026-09-25`<br/>12:21:40 | `support@ifreyr.com`<br/>(Freyr Games 團隊) | 《Star Warfare: Alien Invasion》遊戲資產權利與授權合作詢問 | • 確認原資產著作權主體與授權權限<br/>• 詢問是否考慮授權獨立開發者修改用於新商業遊戲<br/>• 附 GitHub 開發背景 | 🟡 無回覆 |
| **02** | `2026-10-12`<br/>10:00:00 | `support@ifreyr.com`<br/>(Freyr Games 團隊) | 《Star Warfare: Alien Invasion》游戏资产权利与授权合作询问 | • 跟進確認 9/25 信件是否送達<br/>• 請求轉交負責窗口或告知合作意向 | 🟡 無回覆 |
| **03** | `2026-10-19`<br/>10:00:00 | `yxb98yin@gmail.com`<br/>(尹先生 / Google Play) | 《Star Warfare: Alien Invasion》资产授权咨询及联系窗口确认 | • 透過 GP 開發者資訊直洽，確認是否為權利窗口<br/>• 表明願整理專案介紹與素材清單評估 | 🟡 無回覆 |
| **04** | `2026-11-05`<br/>10:00:00 | `yxb98yin@gmail.com`<br/>(尹先生) | Re: 《Star Warfare: Alien Invasion》资产授权咨询及联系窗口确认 | • 表明童年情感投入與尊重原作心血<br/>• 說明 Godot 離線復原成果，爭取實機演示<br/>• 商業化形式與範圍願完全尊重貴方安排 | 🟡 尚待回覆 |

---

## 🛡️ 風險對沖與開發策略連動

```mermaid
flowchart TD
    Inquiry["⚖️ 授權尚未正式回覆<br/>(4 輪寄件完成，無法律正式授權)"] --> Risk["⚠️ 商業侵權潛在風險"]
    
    Risk --> Strategy["🛡️ 專案分軌因應策略 (2026-11-12)"]
    
    Strategy --> MainBranch["🌿 main 分支 (現代化重製)"]
    MainBranch --> MB1["🎨 裝甲全面採獨立自製設計 (新 Viper/Strike/Titan)"]
    MainBranch --> MB2["🚫 移除原版資產商業依賴，自主原創"]

    Strategy --> ClassicBranch["🏛️ codex/classic-hd (1:1 復刻)"]
    ClassicBranch --> CB1["🔒 僅作為離線學習研究與本地復刻跑分"]
    ClassicBranch --> CB2["🚫 不進行公開商用發布與連線盈利"]
```
