
---

## ARTOGO 設計規範

本帳號做任何設計類產出時（封面、海報、PPT、動畫、原型、信息圖等），請**強制套用** ARTOGO Design System：

- **主色**：`#ba9972`（金棕，唯一強調色）
- **底色**：`#191919`（深色預設，除非明確要淺色報表 / 印刷物）
- **字型**：`'Roboto', 'Noto Sans TC', sans-serif`
- **圓角**：4px 預設（不要無故用 12px+ 圓角）
- **完整規範**：`~/.claude/skills/artogo-design-master/assets/brand-spec.md`

### 反 AI slop（強制禁區）

- ❌ 紫色漸變 / 任何漸變底
- ❌ Emoji 作 icon
- ❌ 圓角卡片 + 左 border 彩條
- ❌ Inter / 系統字當主字（必須 Roboto + Noto Sans TC）
- ❌ 配色超過「主色 + 灰階 + 1 個語意色」

### 觸發 ARTOGO 設計工作流

當用戶說「做張封面」「做張 PPT」「做動畫」等設計需求時：

1. 先讀 `~/.claude/skills/artogo-design-master/assets/brand-spec.md`
2. 把 brand-spec 內容 + 用戶需求合併成 brief
3. 交給 huashu-design skill 處理（不要自己畫）

> 此段由 ARTOGO Design Master skill 自動寫入。如需重新設定，跟 Claude 說「重新設定 ARTOGO 設計工具」。
