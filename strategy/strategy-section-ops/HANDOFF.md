# HANDOFF 交接文件 — 策略選股專區營運專案

> 從雲端（Claude Code on the web）session 交接到本地 Claude Code session。
> 目的：本地能用使用者的**神策 skill** 與內部資料權限續作。
> 先讀 `PROJECT-CONTEXT.md`（完整脈絡）＋ `README.md`（總調手冊），再看本檔的狀態與下一步。

---

## 1. 為什麼交接到本地

- 需要連**神策（Sensors Data）**取數、使用者的神策 skill 在**本機 `~/.claude/skills`**。
- 雲端 session 是隔離容器，連不到內部系統、也不該放券商客戶資料。
- 本地有 VPN/金鑰與資料治理控管，是跑真實資料的正確環境。

## 2. 如何在本地接軌

```bash
# 在你本機放這個 repo 的目錄
git fetch origin
git checkout claude/optimize-strategy-section-JHvL0   # 全部產出都在這個分支
git pull origin claude/optimize-strategy-section-JHvL0
```

- 在這個目錄開本地 Claude Code。
- 五個 agent 已轉成可呼叫 subagent：`.claude/agents/strategy-section-*.md`（pm / campaign-planner / performance-analyst / innovation-lab / peer-tracker）。
- 開場可直接貼 `交接prompt-貼到本地對話.md` 的內容，讓本地 AI 秒進入狀況。

## 3. 目前狀態（done）

- ✅ 五個 agent 人物設定（`strategy/strategy-section-ops/*.md`）＋可呼叫 subagent（`.claude/agents/`）。
- ✅ 總調手冊 `README.md`（共同脈絡、KPI 字典、調度圖）。
- ✅ 對主管提案 `提案-現況診斷與過渡期方案.md`（9千→50萬框架、分層 KPI）。
- ✅ `第一個月作戰計畫.md`（已含雙臂修正、對帳戰報旗艦觸點）。
- ✅ `第一週建置與量測規格.md`（分群/保留組/埋點/KPI 定義/法遵關卡/校準清單）。
- ✅ `PROJECT-CONTEXT.md`（AI 完整理解）。

## 4. 待辦 / 下一步（todo）

1. **使用者拍板**：灘頭堡「雙臂修正」（A 臂活躍戶學習慣、B 臂中低頻證交易增量）是否採用。這是策略級反轉，未定前先別發包執行。
2. **（本地＋神策 skill）寫並跑量測查詢**，取彙總數字：
   - A/B 臂分群人數、活化率（推播→進專區）、進專區數
   - 有意義點擊分布、日活鐵粉數（當日≥5 有意義點擊去重）
   - 留存 cohort（D1/3/7/14）
   - 保留組交易差額（B 臂治療 − 保留，筆數與金額）
3. 把第一週規格的**埋點轉成神策事件/屬性設計表**。
4. 視需要：每日對帳戰報＋活化推播**文案範本**（過法遵口吻）、**達標路徑反推試算表**（輸入活化率/留存率→算達 4,200 時程與所需觸及/預算）。

## 5. 交接時務必守住的準則

- 對外訊息（推播/內容/績效揭露）**先過法遵**；揭露績效須附風險與最大回撤、不暗示保證。
- 神策只取**彙總/去識別化**資料，不外洩客戶個資。
- **保留組必須乾淨**（所有通路含營業員名單都排除）。
- 論成效看**交易增量**（B 臂 vs 保留組），不是點擊；點擊漲但交易沒動要吹哨。

## 6. 一句話狀態

地基（脈絡、提案、計畫、第一週規格、agent 團隊）已就緒並 push；**卡在「雙臂修正待拍板」與「需在本地用神策跑出第一批量測數字」**——這兩步完成就能正式進入第二週的內容引擎執行。
