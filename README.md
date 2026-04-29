# ARTOGO Design Master

> 公司專屬 Claude Code skill。同事貼一行指令到 Claude Code 就能裝起來，自動完成 huashu-design 安裝 + ARTOGO 設計規範注入 + 第一次熱身任務。

---

## 這是什麼

一個給 ARTOGO 公司內部使用的 Claude Code 技能（skill），職責有三：

1. **首次設定** — 同事第一次找它時，自動裝好 huashu-design 設計引擎、把 ARTOGO 規範寫進 `~/.claude/CLAUDE.md`、帶他跑一個熱身任務
2. **持續陪伴** — 同事忘記怎麼用 / 出問題時當參考助理
3. **任務轉派** — 同事說「做張封面」時，自動帶 ARTOGO 規範交給 huashu-design 處理

---

## 同事怎麼用

### 第一次安裝（一輩子一次）

請同事打開 Claude Code，在對話框貼這一行：

```
請執行：npx skills add YOUR_GITHUB_USERNAME/artogo-design-master -g --agent claude-code -y
```

> ⚠️ 把 `YOUR_GITHUB_USERNAME` 換成這個 repo 實際擁有者的 GitHub 帳號。

### 第一次設定（5 分鐘）

裝完後，**重啟 Claude Code**，新對話打：

```
我要開始用 ARTOGO 設計工具
```

skill 會自動跳出來引導他完成設定。

### 之後日常使用

直接用日常語言：

- 「做張下週活動的 IG 封面」
- 「做一份提案 PPT 封面」
- 「把這段內容做成多圖」

skill 會接到、套上 ARTOGO 規範、交給 huashu-design 處理。

---

## 檔案結構

```
artogo-design-master/
├── SKILL.md                              ← skill 主檔案（給 Claude 看）
├── README.md                             ← 你正在看這個（給維護者看）
│
├── assets/
│   ├── brand-spec.md                     ← 完整 ARTOGO 設計規範
│   └── claude-md-snippet.md              ← 寫入 ~/.claude/CLAUDE.md 的內容
│
└── references/
    ├── troubleshooting.md                ← 6 種症狀的對症腳本
    ├── faq.md                            ← 9 個常見問題
    └── first-task.md                     ← 3 種熱身任務 brief 模板
```

---

## 維護指南

### 改了 ARTOGO 設計規範要怎麼辦？

1. 編輯 `assets/brand-spec.md`
2. 編輯 `assets/claude-md-snippet.md`（如果改的是強制規則）
3. `git commit` + `git push`
4. 通知同事：「跟 Claude Code 說『升級 ARTOGO 設計工具』」

### 想加新的觸發詞？

編輯 `SKILL.md` 開頭的 `description` 欄位，把新觸發詞加進去（用頓號分隔）。

### 想加新的疑難排解情境？

編輯 `references/troubleshooting.md`，新增一個「症狀 N」段落。

### 想加新的熱身任務選項？

編輯 `references/first-task.md`，新增一個「選項 D」段落，並更新 SKILL.md 的 Step 5 把 D 加進選單。

---

## 測試（push 到 GitHub 前自己先試）

### Local install 測試

在你自己電腦先把這個 skill 裝起來測試：

```bash
# 假設 repo 還沒 push，從本地路徑裝
npx skills add file:///C:/Users/User/Desktop/artogo-design-master -g --agent claude-code -y

# 或 Mac
npx skills add file:///Users/你的帳號/Desktop/artogo-design-master -g --agent claude-code -y
```

裝完後重啟 Claude Code，新對話打「我要開始用 ARTOGO 設計工具」，看會不會跑起來。

### 跑得起來再 push

確認本地測試 OK 後再 `git push` 到 GitHub，避免同事拿到壞掉的版本。

---

## 為什麼是 GitHub 而不是別的

`npx skills` 工具設計上預設從 GitHub 抓 repo。其他方案（zip / 私有 server）成本高很多。

**Public repo 不會洩漏隱私** —— 這個 skill 的內容本來就是要分發給公司同事的，沒有秘密。

---

## 已知限制

- **同事必須先有 Claude Code**：這個 skill 不負責教他裝 Claude Code 本身（見 troubleshooting.md 症狀 1）
- **同事必須會複製貼上指令**：第一次安裝時要貼一行指令到對話框
- **沒有圖形介面**：所有互動都在 Claude Code 對話裡發生

---

## 維護者

- 建立日期：2026-04-29
- 維護者：[你的名字 / 公司]
- 基於：[huashu-design](https://github.com/alchaincyf/huashu-design) by 花叔

---

## 授權

內部使用，請勿外流（如果你不希望它被外流的話）。

或加上 MIT License 公開分享給其他公司使用。
