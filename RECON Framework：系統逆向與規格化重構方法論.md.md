


> **Reference-driven decomposition → specification → reconstruction → validation**

我會把它翻成比較工程化的名字：

# 「拆解 → 建模 → 重構 → 驗證」方法

它的核心思想是：

> **不要叫 AI 直接模仿成品，而是先把成品拆成一組可控制的規格，再讓 AI 根據規格重新實作。**

這個方法其實可以橫跨：

- 電影 / 動畫
    
- 遊戲
    
- UI / UX
    
- Web App
    
- Backend
    
- Game AI
    
- Agent Harness
    
- 美術
    
- 音樂
    
- 整個產品
    

甚至你之前在想的 **Harness v2**，其實也能用完全同一套思維。

---

# 一、先理解「為什麼直接叫 AI 重做」通常很爛

假設你給 AI：

> 「請把 StarCraft Ghost 這段 cinematic 用 2026 畫質重做。」

AI 不知道什麼最重要。

它可能理解成：

```text
StarCraft
+
Marine
+
Zerg
+
modern graphics
```

然後生成一段：

> 「看起來很像 StarCraft 的東西。」

但它未必知道：

- 哪個鏡頭不能改
    
- 哪個角色的動機不能改
    
- 哪個節奏是原作的核心
    
- 哪個 UI 行為才是遊戲體驗
    
- 哪個數值才是平衡的核心
    
- 哪些瑕疵其實是遊戲 identity 的一部分
    

所以：

**AI 直接模仿 = surface imitation**

而我們要做的是：

**decompose → understand system → reconstruct**

---

# 二、真正的核心：你不是在複製「東西」，你在複製「規則」

這是整件事情最重要的一句。

例如：

## 電影

你不是複製：

> 「這一幀長什麼樣子」

而是複製：

```text
故事
角色
情緒
節奏
鏡頭語言
美術語言
聲音
剪輯
```

---

## 遊戲

你不是複製：

> 「這個按鈕長什麼樣子」

而是複製：

```text
Core Loop
Controls
Rules
Economy
Progression
Enemy Behavior
Feedback
Pacing
Meta Game
UX
```

---

## UI

你不是複製：

> 「這個頁面長什麼樣子」

而是複製：

```text
Information hierarchy
Navigation
State
Interaction
Feedback
Error handling
Responsive behavior
```

---

## Agent Harness

你不是複製：

> 「這個 repo 有哪些 markdown」

而是複製：

```text
Instruction hierarchy
State machine
Tool contract
Context policy
Planning
Execution
Validation
Memory
Failure recovery
```

所以它其實是一個很通用的「系統逆向」方法。

---

# 三、我會把這套方法拆成 8 個 Layer

這 8 層就是你之後做任何「重製 / 重構 / remake」的固定模板。

---

# Layer 0 — Source of Truth

先問：

> 我要重建的原始物到底是什麼？

這一層不是分析。

只是把所有 reference 收集起來。

例如：

### StarCraft cinematic

```text
original video
dialogue
subtitle
concept art
character art
music
SFX
official lore
reference cinematic
```

---

### 一個舊遊戲

例如你說的：

**Star Warfare / Call of Mini: Infinity**

可以收：

```text
原版 APK
Gameplay videos
Screenshots
UI screenshots
Wiki
App Store screenshots
玩家錄影
角色資訊
武器資料
關卡資料
音效
原版 UI
原版遊戲流程
```

---

### 一個 Web App

```text
screenshots
video recordings
interaction recording
network behavior
API responses
existing docs
user flows
```

---

# Layer 1 — Decompose

接下來：

> **把成品拆成「最小有意義的單位」。**

這是最關鍵的一步。

---

## 電影

拆成：

```text
Movie
 ├── Scene
 │    ├── Shot
 │    │    ├── Camera
 │    │    ├── Action
 │    │    ├── Lighting
 │    │    └── Audio
```

---

## 遊戲

就不能只拆 Scene。

我要拆成：

```text
Game
│
├── Core Loop
│
├── Controls
│
├── Game Rules
│
├── Player
│
├── Weapons
│
├── Enemies
│
├── AI
│
├── Maps
│
├── Progression
│
├── Economy
│
├── UI
│
├── Audio
│
├── VFX
│
└── Meta systems
```

這個就是遊戲版的「Shot List」。

---

# Layer 2 — Extract Intent

這層非常重要。

因為：

> **你看到的是 implementation，但你要知道它想解決什麼問題。**

例如一個 FPS：

```text
玩家按右鍵
↓
瞄準
```

這只是 implementation。

真正的 intent 可能是：

> 讓玩家在遠距離作戰時犧牲移動速度換取精準度。

所以：

```text
Implementation
    ↓
Intent
```

比單純抄 UI / code 更重要。

---

# 四、拿 Call of Mini: Infinity 來示範

假設今天你的目標是：

> 「把 Call of Mini: Infinity 重構成現代版本」

千萬不要從：

> 「我要重做角色模型」

開始。

我會從：

# Game Experience Map

開始。

例如：

```text
Launch
 ↓
Lobby
 ↓
Select Character
 ↓
Select Weapon
 ↓
Enter Match
 ↓
Kill Enemies
 ↓
Collect Rewards
 ↓
Upgrade
 ↓
Unlock
 ↓
Repeat
```

這就是：

# Core Loop

---

# 五、接著拆「每一個 Loop」

例如：

```text
Combat Loop

Find Enemy
 ↓
Aim
 ↓
Shoot
 ↓
Hit Confirmation
 ↓
Enemy Reaction
 ↓
Enemy Death
 ↓
Reward
```

然後你開始問：

### Aim

- 滑鼠 / touch？
    
- auto aim？
    
- ADS？
    
- aim assist？
    
- sensitivity？
    

### Shoot

- hitscan？
    
- projectile？
    
- fire rate？
    
- recoil？
    
- spread？
    

### Hit

- damage number？
    
- hit marker？
    
- sound？
    
- blood / sparks？
    
- stagger？
    

### Death

- animation？
    
- ragdoll？
    
- dissolve？
    
- explosion？
    

你會突然發現：

> 「遊戲」原來不是一張畫面。

而是一個**狀態機 + 規則系統 + feedback system**。

---

# 六、所以遊戲重構其實應該做「Game Bible」

這個概念跟你前面的 Character Bible 完全一樣。

例如：

```text
GAME_BIBLE.md
```

裡面：

```text
1. Game Vision

2. Core Fantasy

3. Core Loop

4. Controls

5. Combat Rules

6. Weapon Rules

7. Enemy Rules

8. Player Progression

9. Economy

10. Level Design

11. UI/UX

12. Audio

13. VFX

14. Camera

15. Difficulty

16. Session Structure
```

這份文件就是：

> **原遊戲的「規格層」**

而不是：

> 原遊戲的 source code。

這差非常多。

---

# 七、再往下：建立「System Bible」

Game Bible 是：

> 玩家體驗是什麼。

System Bible 是：

> 它怎麼運作。

例如：

## Weapon System

```text
Weapon
 ├── Damage
 ├── Fire Rate
 ├── Magazine
 ├── Reload
 ├── Recoil
 ├── Spread
 ├── Range
 ├── Projectile
 ├── Hit Feedback
 └── Upgrade
```

然後把它寫成 schema：

```text
WeaponDefinition

id
damage
fireRate
magazineSize
reloadTime
range
spread
recoil
projectileType
criticalMultiplier
```

這時候你已經從：

> 「我要重做一把槍」

變成：

> 「我要重建 Weapon System。」

---

# 八、Layer 3：把「體驗」轉成「可實作規格」

這一步就是 AI 最擅長幫你的地方。

假設你觀察到：

> 原遊戲的槍打起來很爽。

這句對 AI 幾乎沒有用。

所以要翻譯：

```text
「爽」
↓
High fire feedback frequency
+
Strong hit confirmation
+
Short time-to-feedback
+
Recoil animation
+
Muzzle flash
+
Impact sound
+
Enemy reaction
+
Camera impulse
```

這個過程就是：

# Experience → Specification

而這個能力才是你真正應該建立的。

---

# 九、Layer 4：建立「Reference Matrix」

這個非常好用。

例如：

|Feature|Original|Intent|Modern Version|
|---|---|---|---|
|Camera|fixed-ish TPS|易於瞄準|dynamic TPS|
|Aim|assisted|mobile friendly|smart aim|
|Weapon|simple|easy access|modular|
|Enemy|wave based|pressure|adaptive spawn|
|UI|old mobile|immediate info|modern HUD|
|VFX|simple|hit feedback|cinematic|
|Progression|grind|retention|shorter progression|

你會發現：

### 不是所有東西都應該 1:1 保留。

這是 remake 最重要的判斷。

---

# 十、我會把「重製」拆成三種層級

這個分類你以後會非常有用。

---

## Type A — Preservation

> 完全保留原本的行為。

例如：

```text
Classic Doom Remake
```

你只是：

```text
higher resolution
better lighting
better animation
```

但：

```text
movement
enemy behavior
weapon behavior
level layout
```

都不改。

---

## Type B — Modernization

保留：

```text
Core fantasy
Core loop
identity
```

改：

```text
UI
controls
graphics
network
performance
QoL
```

這是你說的：

**StarCraft old cinematic → 2026 cinematic**

比較接近這一類。

---

## Type C — Reinterpretation

只保留：

```text
DNA
```

然後重新設計：

```text
systems
controls
graphics
progression
level design
```

例如：

> Call of Mini: Infinity → 2026 stylized extraction shooter

這已經不叫單純 remake，而是：

**reimagining**。

---

# 十一、Layer 5：建立「DNA Map」

這是我最推薦你加入的方法。

對任何舊作品，先問：

> **如果我只能留下 20%，哪 20% 不能失去？**

例如一個遊戲：

```text
Visual DNA
Gameplay DNA
Audio DNA
UX DNA
Social DNA
Progression DNA
Emotional DNA
```

然後：

```text
Star Warfare DNA

Visual:
stylized sci-fi

Combat:
fast arcade shooting

Session:
short

Enemy:
大量敵人

Reward:
頻繁

Camera:
third-person

Fantasy:
one-man-vs-army
```

這些就是：

# Immutable DNA

你之後怎麼現代化都不能亂動。

---

# 十二、Layer 6：Prototype，不要直接 Full Build

這跟你剛才做 StarCraft cinematic 一模一樣。

不要：

> 「我開始重做整個遊戲。」

先做：

# Vertical Slice

例如：

```text
One map
One player
One weapon
One enemy
One boss
One upgrade
One UI loop
```

完整跑：

```text
Login
 ↓
Lobby
 ↓
Start
 ↓
Combat
 ↓
Kill
 ↓
Reward
 ↓
Upgrade
 ↓
Return
```

整個 loop 通了。

才開始擴。

---

# 十三、這跟你做 AI-DM 其實也是完全一樣

你之前問我：

> AI DM 怎麼避免幻覺？

其實也可以用這套。

不要直接：

> 「LLM，請你當 DM。」

而是：

```text
Rule Bible
+
World Bible
+
Character State
+
Quest State
+
Combat State
+
Action Schema
+
Validation
```

然後：

```text
Player Intent
 ↓
Parser
 ↓
Game State
 ↓
Rules Engine
 ↓
LLM Narration
 ↓
State Validation
 ↓
Commit
```

這也是：

**Decompose → Model → Execute → Validate**

---

# 十四、甚至你的 Harness 都可以套

你之前在研究 Claude Code Mentor Harness。

你現在看到這個方法，應該會發現一件很有意思的事情。

你原本可能會想：

> 「我要找一個很好的 harness config。」

但我會改成：

### 先拆「成熟 agent 的行為」

例如：

```text
Input
 ↓
Interpretation
 ↓
Planning
 ↓
Tool selection
 ↓
Execution
 ↓
Validation
 ↓
Recovery
 ↓
Memory
```

然後問：

> 每個階段真正的 intent 是什麼？

再做：

```text
Agent Bible
+
State machine
+
Tool contracts
+
Policies
+
Validation
```

最後才決定：

```text
Claude Agent SDK
OpenAI Agents SDK
LangGraph
custom loop
```

這個思路其實跟遊戲 remake 完全相同。

---

# 十五、所以我會把整套方法正式化成一個 Framework

如果你以後要一直做這種事情，我建議直接把它叫：

# RECON Framework

可以是：

**R — Reference**

收集原始材料。

**E — Extraction**

拆解 behavior / system / visual / rule。

**C — Canonicalization**

整理成：

```text
Bible
Schema
State
Rules
Constraints
```

**O — Orchestration**

決定 AI / tools / runtime 怎麼合作。

**N — Normalization / Validation**

驗證：

> 新版本是否仍然保留原作 DNA？

---

# 十六、實際操作流程

整個 pipeline 可以固定成：

```text
                SOURCE
                   │
                   ▼
          ┌─────────────────┐
          │   REFERENCE     │
          │ video/code/game │
          └────────┬────────┘
                   ▼
             DECOMPOSITION
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
     Visual      System      UX
        │          │          │
        └──────────┼──────────┘
                   ▼
              INTENT MAP
                   │
                   ▼
               DNA MAP
                   │
                   ▼
             SPECIFICATION
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
      Bible       Schema    State
        │          │          │
        └──────────┼──────────┘
                   ▼
               PROTOTYPE
                   │
                   ▼
             VERTICAL SLICE
                   │
                   ▼
               VALIDATION
                   │
          ┌────────┴────────┐
          │                 │
       Preserve          Change
          │                 │
          └────────┬────────┘
                   ▼
               ITERATION
                   │
                   ▼
                SCALE
```

---

# 十七、而 AI 的角色也應該改變

不要讓 AI 當：

> 「幫我做完整遊戲的人。」

讓 AI 分工。

例如：

### Gemini

```text
Researcher
Analyst
Game Designer
Director
Specification Writer
```

### Coding Agent

```text
Implementer
Refactorer
Test Writer
Debugger
```

### Image Model

```text
Concept Artist
Asset Generator
```

### Video Model

```text
Cinematographer
Animator
Previsualization Artist
```

### LLM Validator

```text
QA
Continuity Checker
Spec Checker
Regression Reviewer
```

這就開始變成一個真正的：

# AI Production Pipeline

而不是：

> prompt → hope。

---

# 十八、真正厲害的地方是「Reference ≠ Specification」

這是我最希望你抓住的概念。

例如你看到：

> Call of Mini 的 UI 很簡單。

不能直接變：

```text
「做一個簡單 UI」
```

而要變：

```text
WHY:
降低 combat interruption

RULE:
critical combat info must remain visible

INFORMATION:
HP
ammo
enemy count
skill cooldown

BEHAVIOR:
HUD persists during combat

MODERNIZATION:
support scalable HUD
support controller
support keyboard/mouse
support mobile
```

這樣 AI 才真的有辦法幫你。

---

# 十九、所以你的「重構舊遊戲」其實應該分成三份文件

我非常推薦你未來每做一個作品都先建立這三個：

## ① EXPERIENCE.md

回答：

> 玩家感受到什麼？

例如：

```text
Core Fantasy
Game Loop
Pacing
Emotion
Session length
Difficulty
Reward cadence
```

---

## ② SYSTEMS.md

回答：

> 它怎麼運作？

```text
Combat
Movement
Enemy AI
Weapons
Progression
Economy
Networking
Save
Matchmaking
```

---

## ③ REFERENCE.md

回答：

> 它現在長什麼樣？

```text
Visual style
Camera
UI
Animation
Audio
VFX
Characters
Environment
```

最後再：

```text
MODERNIZATION.md
```

回答：

> 我們準備改什麼？為什麼？

---

# 二十、這樣你就能做出非常清楚的「保留 / 修改 / 新增」矩陣

例如：

|系統|原版|2026 重製|
|---|---|---|
|Combat|保留|改善 feedback|
|Weapon|保留|模組化|
|Enemy|保留 AI personality|改 AI|
|Camera|修改|modern TPS|
|UI|重做|responsive|
|Graphics|重做|modern rendering|
|Progression|修改|降低 grind|
|Economy|重做|fair economy|
|Multiplayer|保留核心|modern networking|
|Audio|重做|spatial audio|

這張表本身就可以成為 AI 的工作 contract。

---

# 二十一、這個方法最終會產生一個很重要的東西

叫：

# **Source → Canonical Model → Target**

例如：

```text
Original Game
      │
      ▼
Canonical Model
      │
      ├── Experience
      ├── Rules
      ├── Systems
      ├── Assets
      ├── UX
      └── Constraints
      │
      ▼
Modern Game
```

這個 **Canonical Model** 是整套方法最有價值的地方。

因為一旦它存在：

你甚至可以同時產生：

```text
Godot version
Unity version
Web version
Mobile version
```

而不是重新研究一次原作。

---

# 二十二、這也解釋了為什麼我說「不要直接用 AI remake」

因為真正的工作其實是：

```text
             理解
              ↓
             抽象
              ↓
             規格化
              ↓
             實作
              ↓
             驗證
```

AI 最擅長的是：

```text
規格 → 實作
```

但真正困難的部分是：

```text
成品 → 規格
```

這個才是 **Reverse Engineering / Systems Analysis / Game Design Analysis**。

而你現在開始注意到這件事情，我認為是非常重要的一步。

---

# 最後，把它濃縮成一句話

以後你看到任何一個「很想重做的東西」：

不要問：

> **「我要怎麼讓 AI 把它做出來？」**

先問：

> **「這個東西到底由哪些不可替代的規則、體驗、系統、視覺語言和約束組成？」**

然後：

```text
原作
 ↓
拆解
 ↓
Intent
 ↓
DNA
 ↓
Canonical Spec
 ↓
Prototype
 ↓
Validation
 ↓
Modernization
 ↓
Scale
```

這套方法可以從 **StarCraft cinematic** 一路套到 **Call of Mini、Star Warfare、TRPG、Godot game、Web App，甚至 Agent Harness**。

而且我覺得你現在最值得做的不是再看更多 AI 工具，而是把這套方法正式變成你自己的 **「Remake / Rebuild Methodology」**。這樣之後你看到任何舊遊戲、舊產品、舊架構，都可以直接套同一套流程，而不是每次重新摸索。