---
name: update-design-doc
description: >
  自動同步更新 U-SAFE_設計文件.html。每次建立新頁面、修改現有功能、或更新設計 tokens 時使用此 Skill。
  觸發情境：完成任何 HTML Demo 頁面開發後、新增或修改設計文件頁面、更新版本紀錄、
  「更新設計文件」、「同步設計文件」、「加入版本紀錄」、「update design doc」。
  即使使用者沒有明確要求，只要有新的開發產出，都應該主動觸發此 Skill 來保持設計文件同步。
---

# Update Design Doc — 自動同步設計文件

每次完成開發工作（新頁面、功能修改、tokens 更新等），都要同步更新兩個檔案：
1. **U-SAFE_設計文件.html** — 專案的核心設計文件
2. **DEV_LOG.md** — 版本變更紀錄

這份 Skill 的目的是確保設計文件永遠反映最新的開發狀態，讓 Jean 隨時能回頭查看每個版本做了什麼。

---

## 設計文件結構

設計文件位於：`/mnt/齊家厝/U-SAFE_設計文件.html`

它是一個單頁式文件應用，結構如下：

### 整體架構
- **TopNav** — 頂部導航列，含系統切換（住戶端/建商端）
- **Sidebar** — 左側選單，兩套（`#sb-resident` / `#sb-developer`）
- **Content** — 中央內容區，每個 `<div class="page" id="xxx">` 是一頁
- **TOC** — 右側目錄，由 `renderToc()` 自動生成

### 現有頁面 ID
住戶端：`r-overview`, `r-design`, `r-onboarding`, `r-auth`, `r-home`, `r-case-detail`, `r-profile`, `r-match`, `r-success`
建商端：`d-overview`, `d-design`, `d-auth`, `d-home`, `d-profile`
共用：`demo-plan`（版本時程）, `r-tokens`（Design Tokens）

### 導航機制
- Sidebar 連結格式：`<a class="sb-link" href="#page-id" onclick="return nav(event,'page-id')">頁面名稱</a>`
- 頁面切換：`goto(pageId)` 函數，隱藏所有 `.page` 再顯示目標頁
- TOC 自動渲染：`renderToc(pageId)` 掃描頁面內的 `h2` 生成目錄

### CSS 變數（Design Tokens）
```css
:root {
  --accent:        #C8A75D;   /* 品牌金 */
  --green:         #CB3B1B;   /* 磚紅 CTA */
  --bg:            #2c2c2c;   /* Dark 模式背景 */
  --t1:            #f5f5f5;   /* Dark 模式主文字 */
}
```

### 常用 CSS 類別
- `.callout` — 強調區塊（有左邊框 accent 色）
- `.card-grid` + `.card` — 卡片網格
- `.ftable-wrap` + `.ftable` — 表格容器
- `.fname` — 表格內的標籤（accent 背景）
- `.fwhy` — 表格內的次要說明文字
- `.lead` — 頁面副標題
- `.eyebrow` — 頁面小標題（在 h1 上方）

---

## 更新流程

每次開發完成後，依序執行以下步驟：

### Step 1：讀取現有設計文件
先用 Read tool 讀取 `U-SAFE_設計文件.html` 的相關區段，了解目前的頁面結構和版本表。

### Step 2：判斷需要更新的內容
根據這次開發的成果，判斷需要更新哪些部分：

| 開發成果 | 設計文件更新 |
|---------|------------|
| 新建 HTML 頁面 | 新增對應的 `<div class="page">` + Sidebar 連結 |
| 修改現有頁面 | 更新對應 page 的內容描述 |
| 更新設計 tokens | 更新 `r-tokens` 頁面 + CSS 變數 |
| 任何開發工作 | 更新 `demo-plan` 頁面的版本表 |

### Step 3：更新版本表（必做）
在 `demo-plan` 頁面的版本表 `<table class="ftable">` 中新增一行，格式：

```html
<tr>
  <td><span class="fname">v{版本號}</span></td>
  <td>{這個版本做了什麼 — 具體描述新增/修改的功能}</td>
  <td class="fwhy">{版本重點，2-4字}</td>
</tr>
```

版本號規則：
- 大版本（新系統/大功能）：v1.0, v2.0
- 小版本（頁面新增/功能修改）：v0.4, v0.5
- 修補版本（修 bug/微調）：v0.3.1, v0.3.2

### Step 4：新增頁面（如果有新頁面）
如果這次開發了新的 Demo 頁面，需要：

1. **在 content 區新增 page div**，放在適當位置（住戶端頁面放在 `r-success` 之後、建商端之前）：
```html
<div class="page" id="{page-id}">
  <div class="eyebrow">{分類名稱}</div>
  <h1>{頁面標題}</h1>
  <p class="lead">{頁面說明}</p>

  <h2>頁面結構</h2>
  <p>描述這個頁面的主要區塊和功能...</p>

  <h2>設計重點</h2>
  <div class="card-grid">
    <div class="card">
      <div class="card-icon">{emoji}</div>
      <div class="card-title">{重點標題}</div>
      <div class="card-desc">{說明}</div>
    </div>
  </div>

  <h2>程式碼變更</h2>
  <div class="callout">
    <strong>檔案：</strong>{檔案名稱}<br>
    <strong>新增/修改：</strong>{具體描述}
  </div>
</div>
```

2. **在 Sidebar 新增連結**，找到對應系統的 sidebar（`#sb-resident` 或 `#sb-developer`），在適當的分類下新增：
```html
<a class="sb-link" href="#{page-id}" onclick="return nav(event,'{page-id}')">{頁面名稱}</a>
```

### Step 5：記錄程式碼變更
在相關頁面中加入「程式碼變更」區塊，用 `.callout` 記錄：
- 新增/修改了哪些檔案
- 使用了什麼技術（React component、CSS 動畫等）
- 關鍵的程式邏輯說明

### Step 6：同步更新 DEV_LOG.md
在 DEV_LOG.md 最上方新增版本紀錄：

```markdown
## v{版本號} — {日期}

### 變更內容
- {具體變更 1}
- {具體變更 2}

### 檔案異動
- `{檔案名}` — {做了什麼}

### 備註
{任何需要記錄的注意事項}
```

### Step 7：驗證
更新完成後，確認：
1. 新頁面的 Sidebar 連結能正確導航
2. 版本表的新行格式正確
3. 所有 HTML 標籤正確關閉
4. DEV_LOG.md 格式一致

---

## 注意事項

- 設計文件是單一 HTML 檔，所有修改都在同一個檔案內完成
- 使用 Edit tool 做精確修改，不要整檔覆寫（檔案超過 2400 行）
- 保持 Dark/Light 雙主題相容（用 CSS 變數，不要寫死顏色）
- 版本號只往上加，不回頭修改舊版本的描述
- 每個 page div 都需要 `eyebrow`、`h1`、`lead` 三個基本元素
- Sidebar 連結的分類標題用 `<div class="sb-cat">{分類名}</div>`
