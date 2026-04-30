# ARTOGO Design System · Brand Spec

> 本檔案是 Notion ADS 的**本機快照**，供無 Notion MCP 連線時使用。
> 正式 source of truth：[Notion ADS](https://www.notion.so/artogotw/ADS-3455135e076e81969e1af54ba3ad37a6)
> 快照版本：ADS v3.0 | 同步日期：2026-04-30

---

## 🎯 核心原則（每次做設計前先讀）

1. **深色為預設**：除非用戶明確要淺色（PDF 報表、印刷物），否則一律以 `#191919` 為畫布底色
2. **金棕為唯一強調色**：`#BA9972` 是 ARTOGO 的識別色——所有 accent / 連結 / 重點 / 圖表主色都用它
3. **配色克制**：主色 + 灰階 + 1 個語意色（success / error / warning），不超過
4. **字型固定**：zh-TW 用 Noto Sans TC、EN 用 Roboto，不要用 Inter / 系統字 / 其他
5. **Token 優先**：使用 ADS 的語意 token（`ads/` 開頭），不要自創數值或抓近似色

---

## 🎨 色彩系統

> ADS 色彩分兩層：`ref/`（原始色票，Figma 用）→ `ads/`（語意別名，設計實作綁定此層）。
> 下方列出 `ads/` 語意層的解析色碼，直接用於 HTML / CSS。

### 主色（Primary）

| Token | Hex | 用途 |
|-------|-----|------|
| `ads/Primary/Primary` | `#BA9972` | 主要按鈕、連結、選中、圖表主色 |
| `ads/Primary/On Primary` | `#0F0C09` | 主色背景上的文字 |
| `ads/Primary/Primary Container` | `#7A654B` | 主色容器背景 |
| `ads/Primary/On Primary Container` | `#FEE3C4` | 主色容器上的文字 |

### 表面色（Surface）— 深色主題

| Token | Hex | 用途 |
|-------|-----|------|
| `ads/Surface/Surface` | `#191919` | 預設畫布 / 卡片表面 |
| `ads/Surface/Surface Container Lowest` | `#000000` | 最底層容器 |
| `ads/Surface/Surface Container Low` | `#191919` | 低層容器 |
| `ads/Surface/Surface Container` | `#353535` | 標準容器（卡片、Panel） |
| `ads/Surface/Surface Container High` | `#424242` | 高層容器 |
| `ads/Surface/Surface Container Highest` | `#595959` | 最高層容器（Popover、Dropdown） |
| `ads/Surface/Surface Bright` | `#4D4D4D` | 亮色表面 |
| `ads/Surface/On Surface` | `#E7E7E7` | 主要文字 / 圖示 |
| `ads/Surface/On Surface Variant` | `#C4C4C4` | 次要文字 |
| `ads/Surface/On Surface Hint` | `#858585` | 提示文字、disabled icon |

### 背景與邊框

| Token | Hex | 用途 |
|-------|-----|------|
| `ads/Background` | `#000000` | 頁面最底層背景（UI 用） |
| `ads/Outline/Outline` | `#858585` | 主要邊框 |
| `ads/Outline/Outline Variant Medium` | `#6D6D6D` | 中間邊框 |
| `ads/Outline/Outline Variant` | `#595959` | 次要邊框 / 分隔線 |

### 語意色（Status Colors）

| Token | Hex | 用途 |
|-------|-----|------|
| `ads/Success/Success` | `#82D28A` | 成功、上升趨勢 |
| `ads/Error/Error` | `#F36363` | 錯誤、下降趨勢 |
| `ads/Warning/Warning` | `#EFCE5A` | 警告 |

### 圖表配色順序

```
['#BA9972', '#82D28A', '#EFCE5A', '#F36363', '#DDB586', '#858585']
```

> 第 1 個一定是金棕主色；超過 6 個分類就警告需要重新設計（資訊太雜）。

---

## 🔤 字型系統

### 字型家族

| 模式 | 字型 |
|------|------|
| zh-TW | **Noto Sans TC** |
| EN | **Roboto** |

```css
font-family: 'Roboto', 'Noto Sans TC', sans-serif;
```

### 字重

| 名稱 | 值 | 使用層級 |
|------|-----|---------|
| Regular | 400 | Body |
| Medium | 500 | Title / Label |
| SemiBold | 600 | Display / Headline |

### Typography Schemes（Desktop）

> 格式：`字級(px) / 行高(px) / 字距(px)`

| 層級 | Token | 尺寸 | 字重 |
|------|-------|------|------|
| **Display Large** | `ads/Display Large` | 57 / 64 / -0.25 | SemiBold 600 |
| **Display Medium** | `ads/Display Medium` | 45 / 52 / 0 | SemiBold 600 |
| **Display Small** | `ads/Display Small` | 36 / 44 / 0 | SemiBold 600 |
| **Headline Large** | `ads/Headline Large` | 32 / 40 / 0 | SemiBold 600 |
| **Headline Medium** | `ads/Headline Medium` | 28 / 36 / 0 | SemiBold 600 |
| **Headline Small** | `ads/Headline Small` | 24 / 32 / 0 | SemiBold 600 |
| **Title Large** | `ads/Title Large` | 18 / 28 / 0 | Medium 500 |
| **Title Medium** | `ads/Title Medium` | 16 / 24 / 0.15 | Medium 500 |
| **Title Small** | `ads/Title Small` | 14 / 20 / 0.1 | Medium 500 |
| **Label Large** | `ads/Label Large` | 14 / 20 / 0.1 | Medium 500 |
| **Label Medium** | `ads/Label Medium` | 12 / 16 / 0.5 | Medium 500 |
| **Label Small** | `ads/Label Small` | 11 / 16 / 0.5 | Medium 500 |
| **Body Large** | `ads/Body Large` | 16 / 24 / 0.5 | Regular 400 |
| **Body Medium** | `ads/Body Medium` | 14 / 20 / 0.25 | Regular 400 |
| **Body Small** | `ads/Body Small` | 12 / 16 / 0.4 | Regular 400 |

---

## 🔘 圓角系統（Shape）

| Token | 值 | 常見用途 |
|-------|-----|---------|
| `Corner/None` | 0px | 無圓角 |
| `Corner/Extra-small` | **4px** | **預設**（Checkbox、Switch、小型元素） |
| `Corner/Small` | 8px | Tag、Badge、Chip |
| `Corner/Medium` | 12px | Card、Input、Select |
| `Corner/Large` | 16px | Dialog、Sheet |
| `Corner/Extra-large` | 28px | 大型卡片 |
| `Corner/Full` | 1000px | 圓形（Pill Button、Avatar） |

> **預設用 4px**——ARTOGO 的克制感很大一部分來自小圓角，不要無故用 12px / 16px。

---

## 🌑 陰影層級（Elevation）

> 每個層級由 2 層 Drop Shadow 疊加：

| 層級 | Shadow 組合 | 適用場景 |
|------|------------|---------|
| **Elevation 1** | `0 1px 2px rgba(0,0,0,0.30)` + `0 1px 3px 1px rgba(0,0,0,0.15)` | 卡片、按鈕 hover |
| **Elevation 2** | `0 1px 2px rgba(0,0,0,0.30)` + `0 2px 6px 2px rgba(0,0,0,0.15)` | Dropdown、浮動卡片 |
| **Elevation 3** | `0 1px 3px rgba(0,0,0,0.30)` + `0 4px 8px 3px rgba(0,0,0,0.15)` | Tooltip、Popover |
| **Elevation 4** | `0 2px 3px rgba(0,0,0,0.30)` + `0 6px 10px 4px rgba(0,0,0,0.15)` | Modal、Dialog |
| **Elevation 5** | `0 4px 4px rgba(0,0,0,0.30)` + `0 8px 12px 6px rgba(0,0,0,0.15)` | 全螢幕覆蓋面板 |

---

## 📐 間距系統（Space）

| ADS Spacer | 值 | 常見用途 |
|-----------|-----|---------|
| `Spacer/4px` | 4px | 圖示與文字間距、微間距 |
| `Spacer/8px` | 8px | 緊湊元件內距 |
| `Spacer/16px` | 16px | 預設內距、表單間距 |
| `Spacer/20px` | 20px | 卡片內距 |
| `Spacer/24px` | 24px | 區塊間距 |
| `Spacer/32px` | 32px | 大型區塊間距 |

### 常用情境

| 情境 | 值 |
|------|-----|
| Card 內距 | 20–24px |
| Grid gutter | 16px 或 24px |
| 頁面邊距（desktop） | 60px |
| 頁面邊距（mobile） | 22px |

---

## ✨ 簽名細節（120% 用力的地方）

這些是 ARTOGO 視覺語言的「臉」，做設計時要特別在這些地方花心思：

1. **金棕色作為呼吸感重點**：不是用大面積金棕底色，而是用 1px 細線 / 小色塊 / 文字 underline 點睛，金棕的氣質才出得來
2. **大號序號 + 細水平線**：標題類視覺常用「超大數字（48–144px）+ 一條 1px 細線」做版印感（參考 ARTOGO Notes 多圖系列）
3. **monospace 路徑 / 程式碼**：用 Roboto Mono 配合金棕色，放在深色 code block，技術內容也保留品牌調性
4. **letter-spacing 分層**：
   - 內文（Body）：0.05em
   - 標籤 / Title：0.15em（對應 Title Medium tracking 0.15）
   - 全大寫眉題：0.25–0.3em（很 ARTOGO）
5. **「」全形引號**：中文用全形，不用 ""（排印細節）

---

## 🚫 反 AI slop（絕對不能做的事）

| 禁區 | 原因 |
|------|------|
| ❌ 紫色漸變 / 任何漸變底 | AI slop，破壞 ARTOGO 克制感 |
| ❌ Emoji 作 icon | ARTOGO 是精品調性，不用 emoji 裝飾 |
| ❌ 圓角卡片 + 左 border accent（彩條） | 過度 Material 化，視覺噪音 |
| ❌ Inter / 系統字當主字 | 必須 Roboto + Noto Sans TC |
| ❌ 圓角 > 8px（除非 Chip / Dialog / Full 形） | 預設 4px，大圓角破壞克制感 |
| ❌ 多色聚類 > 3 種強色 | 主色 + 灰階 + 1 個語意色已上限 |
| ❌ SVG 手畫人臉 / 物件 | 用真實素材或留誠實 placeholder |
| ❌ 裝飾性 icon 每個標題都配 | iconography slop |
| ❌ 編造假數據 / 假 stats | 留 placeholder 等真實資料 |

---

## 🌟 氣質關鍵詞

設計時心中默念這 5 個詞，幫助校準：

```
精品 · 克制 · 深色奢華 · 東方排印 · 設計年鑑感
```

> 「像翻一本好的設計年鑑，不像滑一個 SaaS 落地頁。」

---

## 🛠️ CSS Custom Properties（HTML 設計用）

```css
:root {
  /* Brand Primary */
  --ads-primary: #BA9972;
  --ads-primary-container: #7A654B;
  --ads-on-primary: #0F0C09;
  --ads-on-primary-container: #FEE3C4;

  /* Surface */
  --ads-surface: #191919;
  --ads-surface-container-low: #191919;
  --ads-surface-container: #353535;
  --ads-surface-container-high: #424242;
  --ads-surface-container-highest: #595959;
  --ads-on-surface: #E7E7E7;
  --ads-on-surface-variant: #C4C4C4;
  --ads-on-surface-hint: #858585;

  /* Background */
  --ads-background: #000000;

  /* Outline */
  --ads-outline: #858585;
  --ads-outline-variant: #595959;

  /* Status */
  --ads-success: #82D28A;
  --ads-error: #F36363;
  --ads-warning: #EFCE5A;

  /* Shape */
  --corner-xs: 4px;
  --corner-sm: 8px;
  --corner-md: 12px;
  --corner-lg: 16px;
  --corner-full: 1000px;

  /* Space */
  --space-1: 4px;
  --space-2: 8px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
}
```

### Google Fonts 引入

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;600&family=Roboto+Mono:wght@400;500&family=Noto+Sans+TC:wght@400;500;600&display=swap" rel="stylesheet">
```

### Ant Design Theme Config

```typescript
import { theme } from 'antd';

export const artogoTheme = {
  algorithm: theme.darkAlgorithm,
  token: {
    colorPrimary: '#BA9972',
    colorBgBase: '#191919',
    colorBgContainer: '#353535',
    colorBgElevated: '#424242',
    colorBgLayout: '#191919',
    colorText: '#E7E7E7',
    colorTextSecondary: '#C4C4C4',
    colorTextTertiary: '#858585',
    colorBorder: '#858585',
    colorBorderSecondary: '#595959',
    colorSuccess: '#82D28A',
    colorError: '#F36363',
    colorWarning: '#EFCE5A',
    borderRadius: 4,
    fontFamily: "'Roboto', 'Noto Sans TC', sans-serif",
  },
};
```

---

## ✅ 自檢清單（交付前過一遍）

- [ ] 底色是 `#191919`（Surface）嗎？（除非用戶明確要淺色）
- [ ] 主強調色是 `#BA9972` 嗎？
- [ ] 字型是 Roboto（EN）+ Noto Sans TC（zh-TW）嗎？
- [ ] 預設圓角是 `Corner/Extra-small = 4px` 嗎？
- [ ] 沒有紫色漸變 / emoji icon / 左 border accent 嗎？
- [ ] 配色不超過「主色 + 灰階 + 1 個語意色」嗎？
- [ ] 字級用 ADS Typography Schemes，沒有自創數值嗎？
- [ ] 有至少 1 處「簽名細節」做到 120% 嗎？

過不了任一項 → 改。
