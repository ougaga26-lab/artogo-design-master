# ARTOGO Design Master · Project Handoff

> **給接手這個專案的 AI 助手 / 未來的我看的交接文件**
>
> 上次更新：2026-04-30
> 維護者：ougaga26 (artogo.all@gmail.com)

---

## 一句話總覽

> ARTOGO 公司專屬 Claude Code skill。讓**非工程背景**的同事在 Claude Code 對話框打「ARTOGO 設計大師」，就能自動套用公司設計規範做出視覺產出（封面、PPT、海報、動畫、信息圖、多圖等）。

底層引擎是 `alchaincyf/huashu-design`，這個專案是 huashu-design 的「ARTOGO 品牌包裝層」。

---

## 完整使用鏈（同事的視角）

```
1. 看安裝指南網頁          https://ougaga26-lab.github.io/artogo-design-master/
2. 複製一行 npx 指令貼到 Claude Code
3. 完全關閉 + 重啟 Claude Code
4. 新對話打「ARTOGO 設計大師」
5. Master 自動跑設定 → 安裝 huashu-design → 寫入規範 → 熱身任務
6. 之後做設計直接說：「做張 IG 封面」「做一份 PPT」「做張海報」
```

---

## 線上資源

| 用途 | URL |
|------|-----|
| GitHub repo（同事 npx 安裝來源）| https://github.com/ougaga26-lab/artogo-design-master |
| 安裝指南網頁（GitHub Pages） | https://ougaga26-lab.github.io/artogo-design-master/ |
| 底層 huashu-design skill | https://github.com/alchaincyf/huashu-design |

---

## 完整檔案結構

```
~/Desktop/artogo-design-master/                   ← 開發主目錄（你改檔案的地方）
│
├── SKILL.md                                      ← Claude 看的 skill 定義（觸發詞 + 流程）
├── README.md                                     ← 給維護者看的總覽
├── PROJECT_HANDOFF.md                            ← 這份文件
│
├── assets/
│   ├── brand-spec.md                             ← 完整 ARTOGO 規範（色彩 / 字型 / 間距 / 規範禁區）
│   └── claude-md-snippet.md                      ← 同事 ~/.claude/CLAUDE.md 會被追加的內容
│
├── references/
│   ├── faq.md                                    ← 9 個常見問題（用法查詢時讀）
│   ├── first-task.md                             ← 3 種熱身任務的 brief 模板
│   └── troubleshooting.md                        ← 6 種症狀的對症腳本（疑難排解時讀）
│
└── docs/                                         ← GitHub Pages 部署目錄
    ├── index.html                                ← 主網頁（3 個分頁切換）
    └── cards/                                    ← 6 張 skill 科普卡片（給「了解 Skill」分頁輪播用）
        ├── 01-what-is-skill.html
        ├── 02-how-to-list.html
        ├── 03-trigger.html
        ├── 04-conflicts.html
        ├── 05-manage.html
        └── 06-cross-machine.html  ← 含結尾 CTA 跳回「安裝」分頁（postMessage 機制）
```

**本機另外有兩份**：
- `~/.claude/skills/artogo-design-master/` — 你自己 Claude Code 用的 skill 安裝（從 Desktop 那邊 cp 同步）
- 改檔案後要記得 sync，不然你自己測不到最新版

---

## SKILL.md 設計重點

### 觸發詞（description 欄位內）
```
「ARTOGO Design Master」「ARTOGO 設計大師」「ARTOGO 設計」
「ARTOGO 設定」「ARTOGO 設計規範」「ARTOGO 怎麼用」
「設計大師」「設計 Master」「公司設計工具」
「初始化設計工具」「我要開始用 ARTOGO 設計」「重新設定設計工具」
```

### 場景判斷邏輯（觸發後第一件事）
> **預設行為**：直接進首次設定流程（A）。**不要列 4 選 1 選單**讓同事選「設定 / 看用法 / 修問題 / 做設計」——這是早期版本的設計，後來改掉了。

走別的流程的條件：
| 同事說 | 走哪 |
|-------|------|
| 「ARTOGO 怎麼用」 | B 用法查詢（讀 faq.md） |
| 「跑不起來」「壞了」 | C 疑難排解（讀 troubleshooting.md） |
| 「做張封面/PPT/海報...」 | D 任務轉派（讀 brand-spec.md → 組 brief → 交給 huashu-design） |
| 其他 / 語意不清 | A 首次設定 |

### 首次設定流程（A）— 6 步
1. 打招呼 + 立刻動手（**不要等同事回答 OK，邊講邊跑**）
2. 檢查環境（claude --version / node --version）
3. 安裝 huashu-design（`npx skills add alchaincyf/huashu-design ...`）
4. 寫入 ARTOGO 規範到 `~/.claude/CLAUDE.md`（追加，不覆蓋；已存在則跳過）
5. 熱身任務（A/B/C 三選一：IG 封面 / PPT 封面 / A4 海報）
6. 結語 + 收藏觸發詞

### 任務轉派流程（D）— brief 模板
```
【任務】[同事的需求]
【套用設計系統】ARTOGO Design System
- 主色：#ba9972 / 底色：#191919 / 字型：Roboto + Noto Sans TC
- 完整規範：~/.claude/skills/artogo-design-master/assets/brand-spec.md
【其他】嚴格遵守色彩/字級/間距 token；反 AI slop
```

---

## ARTOGO Design System（brand-spec.md 摘要）

### 強制
- 主色 `#ba9972`（金棕，唯一強調色）
- 底色 `#191919`（深色預設）
- 字型 Roboto + Noto Sans TC
- 圓角 4px
- letter-spacing 0.05em / line-height 1.8（body 預設）

### 反 AI slop（禁區）
- ❌ 紫色漸變 / 任何漸變底
- ❌ Emoji 作 icon
- ❌ 圓角卡片 + 左 border 彩條
- ❌ Inter / 系統字當主字
- ❌ 配色超過「主色 + 灰階 + 1 個語意色」

### 簽名細節（120% 用力的地方）
- 大號序號（48-144px）+ 細水平線分隔
- 金棕色細節（不大面積用，用在 1px 線 / underline / 點睛）
- monospace 路徑用金棕色
- letter-spacing 分層（內文 0.05em / 標籤 0.15em / 全大寫眉題 0.25-0.3em）

---

## 安裝指南網頁（docs/index.html）

### 4 個分頁順序
1. **安裝**（首頁）— 5 步驟安裝指南
2. **應用案例** — 9 個 huashu-design 能力 GIF
3. **了解 Skill** — 6 張科普卡片輪播
4. **版本更新** — Changelog；頂部金色 CTA 含 `npx skills update` 一鍵複製，下方按日期列疊代內容

### 重要互動細節
- Step 02 之後有 **⚠️ 安裝 ≠ 設定** 提示（避免同事以為裝完就結束）
- Step 03 強調 **完全重啟 Claude Code**（這是 90% 同事卡關的原因）
- Step 04 列出 **Claude 自動會做的 4 件事**（檢查環境 / 安裝引擎 / 寫規範 / 熱身）
- Step 05 是 **3 個子步驟 ① ② ③**（指定 cwd / 呼叫 / 開始用）
  - ① 有完整 chat-mockup（folder pills + 輸入框示意）
  - ② 三個觸發詞用 pill 形狀展示
  - ② 有 Ran skill 標籤 mockup + 綠色 ✓ 安裝成功
- Step 05 結尾有實心金色 CTA 按鈕「不確定它能幫我做哪些事？」→ 點了切到應用案例分頁
- 「了解 Skill」分頁的第 6 張卡有金色 callout，CTA 用 postMessage 切回「安裝」分頁

### 技術設計
- 純 HTML + CSS + vanilla JS（無框架）
- Tab 切換用 button data-tab + JS class toggle
- 輪播用 iframe 載入 6 張卡片，scale 0.667 把 1080×1080 縮到 720×720
- iframe 的 CTA 用 `parent.postMessage({type:'switch-tab'})` 跨 frame 通訊
- URL hash 支援 `#install / #showcase / #learn / #changelog`
- 響應式（980 / 720 / 480 三個 breakpoint）
- 字型：Google Fonts CDN（Roboto + Roboto Mono + Noto Sans TC）
- 設計風格嚴守 ARTOGO brand-spec

---

## Git 設定

```
repo:    ougaga26-lab/artogo-design-master
branch:  main
remote:  https://github.com/ougaga26-lab/artogo-design-master.git
auth:    Git Credential Manager（第一次 push 已 cache，後續不用再登入）
GitHub Pages: enabled, source = main branch / docs folder
```

### Commit 歷史（時間順序）
1. `0b4537d` Initial commit: ARTOGO Design Master skill
2. `0a5cd30` Add docs landing page; simplify setup flow
3. `d268e40` Add explore CTA button at Step 05 linking to showcase tab
4. `e37d311` Step 05: rewrite as 3-substep checklist with UI mockups
5. `4099038` Step 05 polish: chat mockup, trigger pills, glowing CTA
6. `7123f6b` Update hero title and intro to emphasize 'ARTOGO 設計大師' trigger
7. `a815a1d` Move '已上線' to start of line 2 in hero title
8. `4bda50f` Add 'Learn Skill' tab with 6-card carousel
9. `16a75f7` Update hero copy and Step 05 ① title
10. `b296215` Reorder nav tabs: 安裝 | 應用案例 | 了解 Skill

---

## 給未來 AI 助手的重要 context

### 用戶背景
- **非工程背景**（Windows 11，需要 plain-Chinese 解釋，避免 jargon）
- 已會：Claude Code 對話、GitHub 網頁版、檔案總管、PowerShell 基本操作
- **不熟**：git CLI / npm / Linux 概念
- 偏好：先給多個選項 + 推薦方向，他選定後再動手；不要一頭扎進去做大招
- 對「設計細節」很敏感（會反覆調整文案 / 視覺 / 排版到滿意）

### 工作流原則
- **Junior Designer 模式**：先 vocalize 思路 + 給變體 + 等確認 → 動手；別自作主張
- **承認誤判**：搞錯了就直接說，不要繞圈圈
- **每次改動 push 後告知**：用戶會去 GitHub Pages 看結果，要 set 1-2 分鐘 rebuild expectation

### 已知坑（避免重蹈我的覆轍）

1. **Claude Code workspace label** = cwd 對應 git repo 的 remote URL 抽出的 repo name
   - 不是 `~/.claude/projects/` folder 名稱
   - 不是 jsonl metadata
   - 是看 GUI 啟動時的 cwd 那個資料夾的 git remote
   - **我為這個 debug 浪費了 4 輪誤判**——記住這條

2. **不要動 ~/.claude/projects/ 下的 jsonl 檔案**
   - 那是 Claude Code 內部對話記錄
   - 動了可能 corrupt 對話列表
   - workspace label 是 baked 在 conversation metadata（IndexedDB / LevelDB），無法後改

3. **本機 sync 用單檔 cp，不要 cp -r 整個資料夾**
   - cp -r 會試圖覆寫 .git/objects/ 下 read-only 檔案 → permission denied
   - 改檔案後只 cp 改的那個檔案就好

4. **GitHub Pages rebuild 要 1-2 分鐘**
   - push 完不要立刻打開頁面
   - 看到 200 OK 不代表 latest 內容已部署（CDN cache）
   - 用 hard refresh（Ctrl+Shift+R）

5. **同事 ≠ 你**
   - 你會用 PowerShell + git，同事連 npx 都不知道
   - 一切 UX 設計以「不熟技術的同事」為標準
   - 寫文案永遠 plain Chinese，不要 jargon

6. **資料夾命名小心混淆**
   - 用戶 Desktop 上 `DESIGN MASTER`（大寫帶空格）≠ `artogo-design-master`（kebab-case）
   - 前者是另一個專案（STOTT-PILATES-EXAM repo），後者是這個專案
   - 用戶曾誤從 DESIGN MASTER 啟動 GUI，導致 workspace label 跑出 STOTT
   - 啟動時要明確選 `artogo-design-master`

### 工作流偏好

| 情境 | 用戶喜歡的回應方式 |
|------|--------------------|
| 規劃新功能 | 給 2-3 個方向選項 + 我推薦哪個 + 為什麼 |
| 動手前 | 「我會做 1, 2, 3，你看著就好」 |
| 動手中 | 每完成一步報告 + 給 preview |
| 完成後 | 簡短總結 + 下一步建議 |
| 出錯時 | 直接承認 + 給修復方案 |

---

## 維護工作流

### 改 brand-spec（規範更新）
```bash
cd "C:/Users/User/Desktop/artogo-design-master"
# 1. 編輯 assets/brand-spec.md
# 2. 編輯 assets/claude-md-snippet.md（如果改的是強制規則）
git add assets/brand-spec.md assets/claude-md-snippet.md
git commit -m "Update brand spec: <變動描述>"
git push

# 3. 同步本機 skill
cp "C:/Users/User/Desktop/artogo-design-master/assets/brand-spec.md" \
   "C:/Users/User/.claude/skills/artogo-design-master/assets/brand-spec.md"

# 4. 通知同事跑：npx skills update artogo-design-master
```

### 改網頁（docs/）
```bash
cd "C:/Users/User/Desktop/artogo-design-master"
# 編輯 docs/index.html 或 docs/cards/*.html
git add docs/
git commit -m "Update docs: <變動描述>"
git push
# 等 1-2 分鐘 → 開 https://ougaga26-lab.github.io/artogo-design-master/ 看
```

### 新增 changelog 條目（每次有更新都做）

只要規範 / SKILL / 流程有任何疊代，**都該在「版本更新」分頁多加一筆**讓同事知道。

**位置**：`docs/index.html` 裡找 `<div class="log-list">`，把新條目**塞在最上面**（最新的在頂端）。

**模板**（直接複製改）：
```html
<article class="log-entry">
  <header class="log-head">
    <div class="log-year">2026</div>
    <div class="log-day-rule">
      <span class="log-day">MM.DD</span>
      <span class="log-rule"></span>
    </div>
  </header>
  <h3 class="log-title">這次更新的一句話標題</h3>
  <ul class="log-items">
    <li class="log-item">
      <span class="log-tech">技術描述（灰色）</span>
      <span class="log-arrow">→</span>
      <span class="log-plain">白話翻譯（亮色，給同事看的）</span>
    </li>
    <!-- 通常 3-5 條 item 為佳，太多看不完 -->
  </ul>
</article>
```

**寫作原則**：
- 左半（tech）：寫實際改了什麼檔案 / token / 流程
- 右半（白話）：寫**對同事而言會發生什麼變化**
- 不要兩邊都寫技術，也不要兩邊都寫白話——對比才有資訊量
- 條目精煉：3-5 條最佳，超過代表更新太雜要拆成兩天

**push 後別忘記**：如果這次更新需要同事重裝，在 commit message / 公司 Slack 也提一下，光看網頁的同事可能漏掉。

### 改 SKILL.md（流程 / 觸發詞）
```bash
cd "C:/Users/User/Desktop/artogo-design-master"
# 編輯 SKILL.md
git add SKILL.md
git commit -m "Update skill: <變動描述>"
git push

# 同步本機
cp "C:/Users/User/Desktop/artogo-design-master/SKILL.md" \
   "C:/Users/User/.claude/skills/artogo-design-master/SKILL.md"

# 重啟 Claude Code 測試
```

---

## 未來可能要做的事

### 短期（用戶可能 1-2 週內想到）
- [ ] **同事使用反饋收集**：問早期使用同事「卡在哪裡」「哪些觸發詞他講了沒反應」
- [ ] **加新熱身任務選項**（除了 IG/PPT/海報，可能還想加 名片 / 提案 / 信息圖）
- [ ] **加新疑難排解情境**（看真實同事踩到什麼坑）
- [ ] **網頁加 FAQ / Troubleshooting 分頁**（如果同事問題太多，把 references/faq.md 內容也展示在網頁）

### 中期（1-3 個月）
- [ ] **歡迎卡片**（裝完設定後，自動生成一張 ARTOGO 風格 welcome 圖放 Desktop，儀式感）—— 早期討論過但沒做
- [ ] **版本號機制**：SKILL.md 加 version 欄位，每次規範更新時 bump，同事 update 看得出版本變化
- [ ] **CHANGELOG.md**：記錄 brand-spec 每次更新的內容
- [ ] **使用統計**：可選，看哪些觸發詞用得多、哪些 case 跑得不好

### 長期（如果 ARTOGO 內部 AI 工具擴大）
- [ ] **公司內部其他 skill**：ARTOGO Dev Master / Writer Master / Brand Master 等，共用 brand-spec
- [ ] **Master 系列入口網**：合併安裝指南，一個 hub 看所有 ARTOGO skill
- [ ] **整合公司訓練流程**：新員工 onboarding 必裝

---

## 風險 / Known Issues

1. **GIF hot-link 風險**：應用案例分頁的 9 個 GIF 都從 `alchaincyf/huashu-design` v2.0 release hot-link。如果上游刪除這些 release assets，網頁的 GIF 全失效。
   - 應對：定期確認上游連結還活著（curl 檢查 200 OK）
   - 永久解：把 GIF 下載到自己的 GitHub release，改 src

2. **GitHub Pages rate limit**：免費 Pages 每月 100GB 流量。同事人數小不會超，但要知道。

3. **同事 npx skills add 失敗的 fallback**：referenced/troubleshooting.md 的「症狀 3」涵蓋了，但實際同事踩坑時可能有未涵蓋情境，要持續 update。

4. **Claude Code 版本相容性**：SKILL.md 寫的指令（`npx skills add ...`）依賴 Claude Code 的 skills CLI。如果 Anthropic 改了 CLI，這個 skill 安裝指令也要對應改。

---

## 備案 / 緊急情況

### 如果 GitHub repo 被誤刪
本機備份在：
- `~/Desktop/artogo-design-master/`（含 .git，可重新 push 到新 repo）
- `~/.claude/skills/artogo-design-master/`（沒 .git，但檔案完整）

### 如果同事的安裝指令突然失效
- 先 check `npx skills` 工具是否有更新（Anthropic 改了 CLI）
- 看本機 `~/.claude/skills/artogo-design-master/` 是否還在
- 如果是 npx 工具改了，更新 SKILL.md / docs/index.html 的安裝指令

---

## 最後的話

這個專案的核心設計哲學是：

> **同事不需要懂技術，只需要會講人話。**
>
> 「做張海報」「幫我做 PPT」「畫張多圖」——這些是同事每天會講的話。
> 我們的工作是讓 Claude Code 聽得懂這些話，並自動套上 ARTOGO 規範交付。
>
> 任何讓同事覺得「我要學新東西才能用」的設計都是失敗的。

接手這個專案時請保持這個原則。每次想加新功能 / 改流程，先問自己：「這個改動會讓同事更容易用，還是更難？」

---

**Good luck. ✨**
