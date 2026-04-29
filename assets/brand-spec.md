# ARTOGO Design System · Brand Spec

> 完整 ARTOGO 視覺規範，供 huashu-design 引擎在做任何 ARTOGO 設計時嚴格遵守。
> 來源：ARTOGO `analytics` (Next.js 16 + AntD 6) & `officialwebsite` (Next.js 12 + AntD 5)
> 採集日期：2026-04-29

---

## 🎯 核心原則（每次做設計前先讀）

1. **深色為預設**：除非用戶明確要淺色（PDF 報表、印刷物），否則一律深色 `#191919` 底
2. **金棕為唯一強調色**：`#ba9972` 是 ARTOGO 的識別色——所有 accent / 連結 / 重點 / 圖表主色都用它
3. **配色克制**：主色 + 灰階 + 1 個語意色（success/error/warning），不超過
4. **字型固定**：Roboto + Noto Sans TC，不要用 Inter / 系統字 / 其他

---

## 🎨 色彩系統

### 品牌主色（Brand Accent）

| Token | Hex | 用途 |
|-------|-----|------|
| `--artogo-primary-accent` | `#ba9972` | 主要按鈕、連結、選中狀態、圖表主色 |
| `--artogo-secondary-accent` | `#ddb586` | Hover 狀態、次要強調 |
| `--artogo-tertiary-accent` | `#fee3c4` | 淺色強調、背景提示 |
| `--artogo-on-accent` | `#191919` | 品牌色上的文字 |

### 深色主題（Dark Theme — 預設）

| Token | Hex | 用途 |
|-------|-----|------|
| `--artogo-bg-base` | `#191919` | 頁面底色 |
| `--artogo-bg-container` | `#353535` | 卡片、容器背景 |
| `--artogo-bg-content` | `#252525` | 內容區域背景（次層） |
| `--artogo-bg-elevated` | `#353535` | Popover、Dropdown |
| `--artogo-bg-hover` | `#4b4b4b` | Hover 背景 |
| `--artogo-text` | `#e7e7e7` | 主要文字 |
| `--artogo-text-secondary` | `#c4c4c4` | 次要文字 |
| `--artogo-text-tertiary` | `#858585` | 說明文字、Icon |
| `--artogo-text-disabled` | `#9a9a9a` | 禁用文字 |
| `--artogo-border` | `#595959` | 主要邊框 |
| `--artogo-border-secondary` | `#4a4a4a` | 分隔線 |
| `--artogo-border-tertiary` | `#6d6d6d` | 次要邊框 |

### 淺色主題（Light Theme — 報表 / PDF 匯出）

| Token | Hex | 用途 |
|-------|-----|------|
| `--artogo-light-bg` | `#FFFFFF` | 背景 |
| `--artogo-light-bg-card` | `#F8F8F8` | 卡片背景 |
| `--artogo-light-text` | `#1A1A1A` | 主要文字 |
| `--artogo-light-text-secondary` | `#666666` | 次要文字 |
| `--artogo-light-border` | `#E8E8E8` | 邊框 |
| `--artogo-light-highlight` | `#FDF8F0` | 強調背景（奶油色） |

### 語意色（Status Colors）

| Token | Hex | 用途 |
|-------|-----|------|
| `--artogo-success` | `#82d28a` | 成功、上升趨勢 |
| `--artogo-error` | `#f36363` | 錯誤、下降趨勢 |
| `--artogo-warning` | `#efce5a` | 警告 |

### 圖表配色順序

```
['#ba9972', '#82d28a', '#efce5a', '#f36363', '#ddb586', '#858585']
```

> 第 1 個一定是金棕主色；第 2-3 個用語意色；超過 6 個分類就警告需要重新設計（資訊太雜）。

### 灰階（Brand Grays）

| Token | Hex |
|-------|-----|
| `--artogo-brand-900` | `#191919` |
| `--artogo-brand-800` | `#353535` |
| `--artogo-brand-700` | `#4a4a4a` |
| `--artogo-brand-600` | `#595959` |
| `--artogo-brand-500` | `#6d6d6d` |
| `--artogo-brand-400` | `#858585` |
| `--artogo-brand-300` | `#949494` |
| `--artogo-brand-200` | `#c4c4c4` |
| `--artogo-brand-100` | `#e7e7e7` |
| `--artogo-brand-050` | `#f0f0f0` |

### 疊加效果（Overlays）

| Token | 值 |
|-------|-----|
| `--artogo-overlay` | `rgba(0, 0, 0, 0.4)` |
| `--artogo-blanket` | `rgba(0, 0, 0, 0.7)` |
| `--artogo-shadow` | `rgba(0, 0, 0, 0.9)` |

---

## 🔤 字型系統

### 字型堆疊

```css
/* 主要字型 */
font-family: 'Roboto', 'Noto Sans TC', sans-serif;

/* CJK 多語言擴展（涉及多語版本時） */
font-family: 'Roboto', 'Noto Sans TC', 'Noto Sans SC', 'Noto Sans JP', 'Noto Sans KR', sans-serif;
```

### 字重

| 名稱 | 值 | 使用場景 |
|------|-----|---------|
| Regular | 400 | 內文、說明 |
| Medium | 500 | 標籤、次標題 |
| Semibold | 600 | 按鈕文字 |
| Bold | 700 | 標題 |

### 字級（Font Size Scale）

| Level | Size | 典型用途 |
|-------|------|---------|
| `--font-00` | 9px | 極小標註 |
| `--font-01` | 12px | 最小可讀文字、Badge |
| `--font-02` | 14px | 正文（預設）、表格 |
| `--font-03` | 16px | 段落強調、Section 標題 |
| `--font-04` | 18px | H3 子標題 |
| `--font-05` | 20px | H2 |
| `--font-06` | 24px | H2 大標 |
| `--font-07` | 28px | H1 報表標題 |
| `--font-08` | 32px | 封面標題 |
| `--font-09` | 36px | 大型 Hero |
| `--font-10` | 48px | 最大展示 |

### 全域排版預設

```css
body {
  font-size: 14px;
  letter-spacing: 0.05em;
  line-height: 1.8;
}
```

---

## 📐 間距系統

| Token | 值 | 用途 |
|-------|-----|------|
| `--space-0` | 0px | — |
| `--space-050` | 2px | 微調 |
| `--space-100` | 4px | 元素內小間距 |
| `--space-150` | 6px | 緊密排列 |
| `--space-200` | 8px | 元素間間距 |
| `--space-300` | 12px | 小區塊間距 |
| `--space-400` | 16px | 標準 gutter |
| `--space-600` | 24px | 大區塊間距、Content padding |
| `--space-800` | 32px | Section 間距 |
| `--space-1200` | 48px | 大型 Section / 報表 |
| `--space-1600` | 64px | 頁面級間距 |
| `--space-2400` | 96px | 超大間距 |

### 常用組合

| 情境 | 值 |
|------|-----|
| Card 內距 | 20–24px |
| Grid gutter | `[16, 16]` 或 `[24, 24]` |
| Section 間距 | 24px (vertical) |
| 頁面邊距（desktop） | 60px |
| 頁面邊距（mobile） | 22px |

---

## 🔘 圓角

| Token | 值 | 用途 |
|-------|-----|------|
| `--radius-100` | 4px | 預設（AntD token） |
| `--radius-200` | 8px | Content area、中型元件 |
| `--radius-400` | 16px | 大型元件 |
| `--radius-full` | 9999px | 膠囊形、圓形按鈕 |

> 預設 4px——ARTOGO 的克制感很大一部分來自小圓角，**不要無故用 12px / 16px 圓角**。

---

## 🌑 陰影

| 元件 | 值 |
|------|-----|
| Card 預設 | `0 1px 4px rgba(0, 0, 0, 0.2)` |
| Card Hover | `0 4px 16px rgba(0, 0, 0, 0.35)` |
| Sider | `2px 0 8px rgba(0, 0, 0, 0.3)` |

---

## 📋 元件規範

### 按鈕

| 類型 | 樣式 |
|------|------|
| Primary | `bg: #ba9972`, `border: #ba9972`, `text: #191919` |
| Default (dark) | `bg: #353535`, `border: #595959`, `text: #e7e7e7` |
| Link | `color: #ba9972`，無背景無邊框 |
| Disabled | `bg: #595959`, `text: #9a9a9a` |

### 卡片

- 背景：`#353535`
- 邊框：無（靠陰影區分層級）
- 圓角：4px
- Hover：陰影增強 + 微上移

### 圖表（Recharts）

| 屬性 | 值 |
|------|-----|
| 線寬 | 2px |
| 主色 | `#ba9972` |
| 副色 | `#82d28a` |
| Grid | `stroke: #4a4a4a`, `strokeDasharray: "3 3"` |
| Axis tick | `fill: #858585` |
| Tooltip 背景 | `#353535` |
| Tooltip 邊框 | `1px solid #595959` |
| Tooltip 文字 | `#e7e7e7` |
| Bar 圓角 | `[4, 4, 0, 0]`（top） |
| 圖表高度 | 260–300px |

---

## ✨ 簽名細節（120% 做到的地方）

這些是 ARTOGO 視覺語言的「臉」，做設計時要特別在這些地方花心思：

1. **金棕色作為呼吸感重點**：不是用大面積金棕底色，而是用 1px 細線 / 小色塊 / 文字 underline 點睛，金棕的氣質才出得來
2. **大號序號 + 細水平線**：標題類視覺常用「超大數字（48-144px）+ 一條 1px 細線」做版印感（參考 ARTOGO Notes 多圖系列）
3. **monospace 路徑 / 程式碼**：用 Roboto Mono 配合金棕色，放在深色 code block，技術內容也保留品牌調性
4. **letter-spacing 0.05em-0.3em 分層**：
   - 內文：0.05em（基礎）
   - 標籤 / 小標：0.15em
   - 全大寫眉題：0.25-0.3em（很 ARTOGO）
5. **「」全形引號**：中文用全形，不用 ""（這是排印細節）

---

## 🚫 禁區（絕對不能做的事）

ARTOGO 的識別感很大一部分來自「不做什麼」：

| 禁區 | 原因 |
|------|------|
| ❌ 紫色漸變 / 任何漸變底 | AI slop，破壞 ARTOGO 克制感 |
| ❌ Emoji 作 icon | ARTOGO 是精品調性，不用 emoji 裝飾 |
| ❌ 圓角卡片 + 左 border accent（彩條） | 過度 Material 化，視覺噪音 |
| ❌ Inter / 系統字當主字 | 必須 Roboto + Noto Sans TC |
| ❌ 圓角 > 8px（除非膠囊形按鈕） | 預設 4px，大圓角會破壞克制感 |
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

## 🛠️ 技術範本（可直接複製進專案）

### Ant Design Theme Config

```typescript
import { theme } from 'antd';

export const artogoTheme = {
  algorithm: theme.darkAlgorithm,
  token: {
    colorPrimary: '#ba9972',
    colorBgBase: '#191919',
    colorBgContainer: '#353535',
    colorBgElevated: '#353535',
    colorBgLayout: '#191919',
    colorText: '#e7e7e7',
    colorTextSecondary: '#c4c4c4',
    colorTextTertiary: '#858585',
    colorBorder: '#595959',
    colorBorderSecondary: '#4a4a4a',
    colorSuccess: '#82d28a',
    colorError: '#f36363',
    colorWarning: '#efce5a',
    borderRadius: 4,
    fontFamily: "'Roboto', 'Noto Sans TC', sans-serif",
  },
  components: {
    Card: { colorBgContainer: '#353535' },
    Table: {
      colorBgContainer: '#353535',
      headerBg: '#353535',
      rowHoverBg: '#3a3a3a',
      borderColor: '#4a4a4a',
    },
    Menu: {
      darkItemBg: '#191919',
      darkItemSelectedBg: 'rgba(186, 153, 114, 0.15)',
    },
    Layout: {
      siderBg: '#191919',
      headerBg: '#353535',
      bodyBg: '#191919',
    },
    Button: {
      defaultBg: '#353535',
      defaultBorderColor: '#595959',
    },
    Segmented: {
      itemSelectedBg: '#ba9972',
      itemSelectedColor: '#191919',
    },
  },
};
```

### CSS Custom Properties（HTML 設計用）

```css
:root {
  /* Brand */
  --artogo-gold: #ba9972;
  --artogo-gold-light: #ddb586;
  --artogo-gold-pale: #fee3c4;

  /* Background */
  --artogo-bg-base: #191919;
  --artogo-bg-container: #353535;
  --artogo-bg-content: #252525;
  --artogo-bg-elevated: #353535;
  --artogo-bg-hover: #4b4b4b;

  /* Text */
  --artogo-text: #e7e7e7;
  --artogo-text-secondary: #c4c4c4;
  --artogo-text-tertiary: #858585;
  --artogo-text-disabled: #9a9a9a;

  /* Border */
  --artogo-border: #595959;
  --artogo-border-secondary: #4a4a4a;
  --artogo-border-tertiary: #6d6d6d;

  /* Status */
  --artogo-success: #82d28a;
  --artogo-error: #f36363;
  --artogo-warning: #efce5a;

  /* Spacing */
  --space-100: 4px;
  --space-200: 8px;
  --space-300: 12px;
  --space-400: 16px;
  --space-600: 24px;
  --space-800: 32px;
  --space-1200: 48px;

  /* Radius */
  --radius-100: 4px;
  --radius-200: 8px;
  --radius-400: 16px;
  --radius-full: 9999px;
}
```

### Google Fonts 引入

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;600;700&family=Roboto+Mono:wght@400;500&family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
```

---

## ✅ 自檢清單（交付前過一遍）

做完設計交付前，huashu-design 應該對照這份清單自檢：

- [ ] 底色是 `#191919` 嗎？（除非用戶明確要淺色）
- [ ] 主強調色是 `#ba9972` 嗎？
- [ ] 字型是 Roboto + Noto Sans TC 嗎？
- [ ] 圓角是 4px 嗎？
- [ ] 沒有紫色漸變 / emoji icon / 左 border accent 嗎？
- [ ] 配色不超過「主色 + 灰階 + 1 個語意色」嗎？
- [ ] 有至少 1 處「簽名細節」做到 120% 嗎？

過不了任一項 → 改。
