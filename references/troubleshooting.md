# 疑難排解 · Troubleshooting

> 給 ARTOGO Design Master skill 在同事遇到問題時參考。
> 原則：**先問清楚症狀，不要丟一堆可能性**。對症下藥。

---

## 症狀 1 · `claude --version` 失敗

### 同事看到的畫面
- Terminal 出現紅字英文
- 或者 Claude 回「找不到指令」

### 通常原因
Claude Code 沒裝。

### 對話腳本

> 「看起來你還沒裝 Claude Code。我帶你裝：
>
> 1. 打開瀏覽器，去 **claude.ai/code**
> 2. 下載對應你電腦的版本（Mac / Windows）
> 3. 跟著安裝精靈一路按下一步
> 4. 裝完之後，**重新打開 Claude Code**，再回來找我說「我裝好了」
>
> 大概 3 分鐘搞定，遇到任何畫面卡住直接拍照給我看。」

---

## 症狀 2 · `node --version` 失敗

### 同事看到的畫面
- 紅字 `'node' is not recognized` 或 `command not found: node`

### 通常原因
Node.js 沒裝。

### 對話腳本

> 「Node.js 是 Claude Code 內部會用到的小工具，需要先裝：
>
> 1. 打開瀏覽器，去 **nodejs.org**
> 2. 點首頁那個綠色大按鈕「**LTS**」（不要點 Current）
> 3. 下載完，雙擊安裝檔，一路按下一步（**勾選『Add to PATH』那項一定要勾**）
> 4. 裝完**重開** Claude Code（很重要，不重開讀不到）
> 5. 回來跟我說「我裝好了」
>
> 大概 5 分鐘。」

---

## 症狀 3 · `npx skills add` 跑到一半卡住或失敗

### 同事看到的畫面
- 跑了很久沒反應
- 或紅字英文（可能是 timeout / network error / EACCES 等）

### 判斷流程

**先問**：「有看到任何紅色文字嗎？把整段複製給我看一下。」

接著按錯誤類型分類：

| 錯誤關鍵字 | 原因 | 解法 |
|----------|------|------|
| `ENOTFOUND` / `network` / `timeout` | 網路問題 | 確認網路通；公司網路可能擋 GitHub → 換熱點再試 |
| `EACCES` / `permission` | 權限問題 | Mac 跑時前面加 `sudo`（Mac only）；Windows 用系統管理員開 PowerShell |
| `404` / `not found` | repo 不存在 / 名字打錯 | 確認 GitHub repo 名稱拼寫 |
| `not a valid skill` | repo 內容缺 SKILL.md | 不是同事的問題，是 skill 維護者問題 → 反映給管理員 |

### 對話腳本（給網路問題的範例）

> 「看起來是網路擋住了 GitHub。試試看：
>
> 1. 把網路切到手機熱點（公司 WiFi 有時會擋）
> 2. 再讓我重跑一次 npx 指令
>
> 還是不行的話，可能是公司防火牆設定，要請 IT 同事白名單 GitHub。」

---

## 症狀 4 · 裝完了但「ARTOGO Design Master」不會自動跳出來

### 通常原因
- 沒重啟 Claude Code（最常見）
- 觸發詞太隱晦（同事說的話沒有對到觸發詞）

### 對話腳本

> 「兩個常見原因：
>
> 1. **沒重啟**：Claude Code 沒重啟讀不到新 skill。請完全關閉再重開（不是只關視窗）。
> 2. **觸發詞**：直接說「**ARTOGO Design Master**」或「**ARTOGO 設定**」，明確一點。
>
> 如果還是不行，跑一下 `npx skills ls -g` 看看清單裡有沒有 `artogo-design-master`，沒有的話就是裝失敗，回去重裝。」

---

## 症狀 5 · 裝好了但做設計時沒有套用 ARTOGO 規範

### 通常原因
- `~/.claude/CLAUDE.md` 沒寫入指引
- 或寫入了但 huashu-design 沒讀到

### 檢查流程

1. 讀 `~/.claude/CLAUDE.md`，確認裡面有沒有 `## ARTOGO 設計規範` 這段
2. 沒有 → 跑「重新設定」流程，重新觸發 setup skill 的 Step 4
3. 有 → 問同事是不是用了 huashu-design 之外的方式做設計（例如直接打開瀏覽器寫 HTML）

### 對話腳本

> 「我幫你檢查一下設定檔...（讀 CLAUDE.md）
>
> [情況 A：缺指引]
> 找到問題了，CLAUDE.md 裡缺 ARTOGO 規範指引。我來幫你寫入，重來一遍。
>
> [情況 B：指引在但沒套用]
> 設定 OK。試試看用「**做張 ARTOGO 風格的 [需求]**」這樣的句子，明確帶上「ARTOGO 風格」這四個字，huashu-design 就會優先讀規範。」

---

## 症狀 6 · 同事說「壞了」但講不清楚發生什麼事

### 對話腳本

> 「沒關係，我們慢慢來。先告訴我：
>
> 1. 你剛剛在打什麼？（複製給我看）
> 2. 你期待會發生什麼？
> 3. 實際發生什麼？（拍個畫面給我看）
>
> 三個都告訴我，我幫你判斷是哪一類問題。」

---

## 通用對話原則

- ❌ 不要丟英文 stack trace 給同事
- ❌ 不要假設同事懂「PATH」「permission」「dependency」這些詞
- ✅ 把錯誤翻譯成「發生了什麼事」+ 「下一步該怎麼做」
- ✅ 一次給一個動作，不要列五個讓他選
- ✅ 講人話：「重新打開 Claude Code」而不是「重啟 client」
