# 齊家厝 U-SAFE Cloud — 專案開發規則

## 基本資訊
- 產品名稱：中文「齊家厝」英文「U-SAFE」
- 技術：單一 HTML + React + Tailwind CDN（快速迭代用，之後遷移 Next.js）
- 版本管理：DEV_LOG.md（非 Git）
- 每版 HTML 獨立命名，放在 `demos/` 資料夾
- Demo 帳密：demo@usafe.tw / usafe2026

## 資料夾結構
```
齊家厝/
├── assets/images/       # Logo（logo-white.png、logo-dark.png）
├── assets/videos/       # Hero 影片（cover.mov、hero-video.mp4）
├── brand/               # 品牌色系參考（html + png）
├── demos/               # 各版本 Demo HTML
├── docs/                # 文件（docx、pdf、流程圖）
│   └── figjam/          # Figjam 匯出 PDF
├── tokens/              # Figma Design Tokens
├── CLAUDE.md            # 本檔案
├── DEV_LOG.md           # 版本變更紀錄
└── U-SAFE_設計文件.html # 設計文件（版本表 + 頁面規格）
```

## 設計文件同步規則（必遵守）

**每次完成開發工作後，必須同步更新以下兩個檔案：**

### 1. U-SAFE_設計文件.html — 版本表 + 頁面

在 `demo-plan` 頁面的 `<table class="ftable">` 版本表中新增一行：
```html
<tr>
  <td><span class="fname">v{版本號}</span></td>
  <td>{具體描述新增/修改的功能}</td>
  <td class="fwhy">{2-4字重點}</td>
</tr>
```

如果有新頁面，還需要：
- 在 content 區新增 `<div class="page" id="{page-id}">` （含 eyebrow、h1、lead）
- 在對應 Sidebar（`#sb-resident` 或 `#sb-developer`）新增連結：
  `<a class="sb-link" href="#{id}" onclick="return nav(event,'{id}')">{名稱}</a>`

### 2. DEV_LOG.md — 變更紀錄

在最上方新增：
```markdown
## v{版本號} — {日期}
### 變更內容
- {變更 1}
### 檔案異動
- `{檔案名}` — {做了什麼}
```

### 版本號規則
- 大功能：v1.0, v2.0
- 頁面新增/修改：v0.4, v0.5
- 修 bug/微調：v0.3.1

### 設計文件結構快速參考
- 頁面格式：`<div class="page" id="xxx">`
- 導航：`goto(pageId)` / `nav(event, pageId)`
- CSS 類別：`.callout`（強調）、`.card-grid + .card`（卡片）、`.ftable`（表格）、`.fname`（標籤）、`.fwhy`（說明）
- 現有頁面：r-overview, r-design, r-onboarding, r-auth, r-home, r-case-detail, r-profile, r-match, r-success, d-overview, d-design, d-auth, d-home, d-profile, demo-plan, r-tokens

## 品牌色系（以 Figma 為準）
- bg-brand: #FFB200（品牌金）
- bg: #F8F5EA（Light 背景）/ #2C2C2C（Dark 背景）
- CTA: #CB3B1B（磚紅）
- 活力色：Teal #2AA39F、Sky #4A90D9
- CSS 變數定義在設計文件的 `:root` 區塊

## 風格
大氣、傳承、柔和、30-40年傳承感。目標用戶為 50-70 歲老屋屋主。
