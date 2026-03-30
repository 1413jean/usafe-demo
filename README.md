# U-SAFE 齊家厝

> 讓都更這條路，不再孤單走。

**U-SAFE 齊家厝** 是一個為 50-70 歲老屋屋主打造的都更資訊透明化平台，透過 AI 輔助風險評估、建商媒合與進度追蹤，讓都市更新的每一步都安心、可查、有依靠。

## Demo

**線上展示：** https://1413jean.github.io/usafe-demo/

| 頁面 | 連結 |
|------|------|
| Landing Page（最新版） | [usafe-landing-v2.0.html](https://1413jean.github.io/usafe-demo/demos/usafe-landing-v2.0.html) |
| 免費評估精靈 | [usafe-evaluate.html](https://1413jean.github.io/usafe-demo/demos/usafe-evaluate.html) |
| 都更進度儀表板 | [usafe-dashboard.html](https://1413jean.github.io/usafe-demo/demos/usafe-dashboard.html) |
| 屋主故事（部落格文章） | [usafe-story.html](https://1413jean.github.io/usafe-demo/demos/usafe-story.html) |
| 屋主故事（列表頁） | [usafe-blog.html](https://1413jean.github.io/usafe-demo/demos/usafe-blog.html) |

**Demo 帳號：** `demo@usafe.tw` / `usafe2026`

## 功能特色

- **AI 風險快篩** — 輸入地址即時評估都更可行性
- **建商媒合** — 根據案件條件推薦合適建商
- **進度追蹤** — 7 階段都更進度即時掌握
- **屋主故事** — 真實案例分享，建立信任感
- **三階會員制** — 免費 / 進階推薦 / VIP，循序漸進

## 技術

目前為快速迭代階段，採用單一 HTML 檔 + CDN 架構：

- React 18（CDN）
- Tailwind CSS（CDN）
- Vanilla JavaScript（Spring 動畫、IntersectionObserver）
- 預計後期遷移至 Next.js

## 品牌色系

| 色彩 | 色碼 | 用途 |
|------|------|------|
| 品牌金 | `#FFB200` | 品牌主色、CTA |
| 暖米背景 | `#F8F5EA` | Light 模式背景 |
| 磚紅 | `#CB3B1B` | 強調、重點按鈕 |
| Teal | `#2AA39F` | 活力色、步驟指示 |
| Sky | `#4A90D9` | 輔助色 |

## 資料夾結構

```
齊家厝/
├── assets/images/       # Logo 與頁面圖片
├── assets/videos/       # Hero 影片素材
├── brand/               # 品牌色系參考
├── demos/               # 各版本 Demo HTML
├── docs/                # 產品文件、流程圖
├── tokens/              # Figma Design Tokens
└── DEV_LOG.md           # 版本變更紀錄
```

## 設計風格

大氣、傳承、柔和 — 帶有 30-40 年歲月感的溫暖設計語言，讓長輩也能安心使用。

---

Built with care for Taiwan's urban renewal future.
