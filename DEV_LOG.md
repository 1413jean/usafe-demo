## v2.6 — 2026-03-30
### 變更內容
- 評估頁面 `.warm-note` 備註區塊背景從白底 `var(--bg-alt)` (#FFFFFF) 改為 `var(--bg)` (#F5F5F5)，與表單卡片形成層次但不再突兀
- 全站 Nav「登入」按鈕（桌面 + 手機版）統一改為直接前往 Dashboard（usafe-dashboard.html），不再跳轉評估頁
- 涵蓋頁面：landing、blog、story、evaluate 共 4 頁 × 2 按鈕 = 8 處修改

### 檔案異動
- `demos/usafe-evaluate.html` — warm-note 背景改 var(--bg)；登入按鈕改連 dashboard
- `demos/usafe-landing-v2.0.html` — 登入按鈕改連 dashboard
- `demos/usafe-blog.html` — 登入按鈕改連 dashboard
- `demos/usafe-story.html` — 登入按鈕改連 dashboard

## v2.5 — 2026-03-30
### 變更內容
- Landing page 跑馬燈 (Marquee) 全面重寫為 requestAnimationFrame 引擎，對齊用戶自訂 Framer ScrollMarquee 元件邏輯
- 移除舊的 CSS `@keyframes marqueeScroll` 動畫與 `.marquee-track.reverse` class 切換機制
- 新引擎參數：baseSpeed 40px/s、scrollMultiplier 0.2、reverseOnScrollUp true
- 滾動速度偵測：監聽 scroll 事件計算瞬時速度（px/s），影響跑馬燈速度 `speed = 40 + |scrollVelocity| × 0.2`
- 方向切換：往下滑 → 向左跑、往上滑 → 向右跑（direction 在停止滾動後保持）
- 速度衰減：scroll velocity 以 `0.95^(dt×60)` 平滑衰減歸零
- 無縫循環：translateX 超過半段內容寬度時自動回繞
- Lazy measure：首次 tick 時才量測 contentWidth，確保字型載入後取得正確尺寸

### 檔案異動
- `demos/usafe-landing-v2.0.html` — marquee CSS 簡化（移除 keyframes，保留 will-change: transform）；JS 全面改寫為 rAF 引擎

## v2.4 — 2026-03-30
### 變更內容
- 新增部落格列表頁（usafe-blog.html）— family.co/blog 風格：垂直清單、分隔線、無圖片
- 頁首「屋主故事」+ 副標 + 篩選 pills（全部/成功案例/都更知識/屋主心聲）
- 7 篇文章條目，第一篇連結至 usafe-story.html
- Story 頁（usafe-story.html）全面重寫為 family.co 乾淨部落格風格 — 窄欄（780px）、text-first、無 Hero cover
- 麵包屑導覽（首頁 > 屋主故事 > 三代同堂的家）
- 文章段落：老屋的困境、踏出第一步、整合與媒合、漫長但值得的等待、嶄新的家、給正在猶豫的你
- 金色邊框 blockquote、圓角圖片含 caption、簡潔時間線列表
- Dashboard（usafe-dashboard.html）全面重寫為 UberEats feed 風格 — 左側 sidebar（220px 純文字無 icon）+ 主要 feed
- 區塊：歡迎、案件狀態 pill、為您推薦的建商（水平捲動卡片）、成功案例精選、附近都更案件、熱門都更區域 pills、都更知識
- 新增登出功能回到首頁
- 行動版：底部 tab bar（純文字無 icon）
- 全站 Nav 統一：所有頁面使用相同 pill nav、相同連結、移除「回首頁」
- Nav mobile menu 修復：`.nav-links` 移出 `<nav>` 外層避免 transform containing block 問題
- Nav mobile menu 新增 × 關閉按鈕
- 屋主故事加入 Nav 第一個連結（連向 usafe-blog.html）

### 檔案異動
- `demos/usafe-blog.html` — 新增，部落格列表頁
- `demos/usafe-story.html` — 全面重寫為乾淨部落格文章風格
- `demos/usafe-dashboard.html` — 全面重寫為 UberEats feed 風格
- `demos/usafe-landing-v2.0.html` — Nav 統一（加入屋主故事連結、mobile menu 修復、× 關閉按鈕）
- `demos/usafe-evaluate.html` — Nav 升級為完整 pill nav（含 mobile fullscreen menu）

## v2.3 — 2026-03-30
### 變更內容
- 新增成功案例深度頁面（owner story / case study），沉浸式捲動敘事
- Hero 全寬照片 + 暗色漸層覆蓋 + 案例標題「三代同堂的家，重獲新生」
- Before 區塊：老屋大圖 + 屋主引言（大號 serif）+ 4 格屋況統計（屋齡42年/35坪/12戶/漏水壁癌）
- Journey 區塊：5 階段垂直時間軸（icon-design 紅色線 + 編號圓點 + spring stagger 動畫），中間插入施工照片
- After 區塊：新大樓大圖 + 新舊對比並排（桌機雙欄/手機堆疊）+ 改建後統計（0年/45坪+10/12F/+180%）+ 屋主引言
- Key Takeaways：3 張洞見卡片（早期整合/選對建商/透明資訊）
- 情感 CTA 區塊 + 金色按鈕導向免費評估頁
- 完全對齊 v2.0 設計語言：CSS tokens、pill nav（glassmorphism + scroll shrink）、ink SVG filters、fade-up IntersectionObserver 動畫、mobile fullscreen menu（nav-links 在 nav 外）、footer
- 全響應式（桌機/平板/手機）

### 檔案異動
- `demos/usafe-story.html` — 新增，成功案例深度頁面
- `DEV_LOG.md` — 新增 v2.3 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v2.3

## v2.2 — 2026-03-30
### 變更內容
- 新增住戶端登入後都更進度儀表板頁面（post-login dashboard）
- 左側 Sidebar 導航（案件總覽/進度追蹤/文件中心/訊息通知/我的資料）+ 行動版底部 Tab Bar
- 7 階段水平進度追蹤器（免費評估→住戶整合→建商媒合→政府審議→核定發布→動工興建→完工交屋），含 spring 動畫進度條填充、current step 脈搏發光
- 歡迎橫幅（金色漸層左邊框）+ 4 欄快速統計卡片
- 最近動態垂直時間軸（5 筆事件，teal/grey 色點區分新舊）
- 重要文件列表（4 份文件，查看按鈕含 Demo 模式 tooltip）
- 服務團隊 3 人聯絡卡片（水平捲動）
- 下一步溫暖提示卡片
- Demo 模式：預填陳太太（demo@usafe.tw）案件 UR-2024-0847 資料
- 全響應式：桌機 sidebar / 平板單欄 / 手機底部 tab bar + 垂直 stepper
- 設計語言完全對齊 v2.0 Landing 與 evaluate 頁面（CSS tokens、spring 動畫、card 風格）

### 檔案異動
- `demos/usafe-dashboard.html` — 新增，住戶端都更進度儀表板
- `DEV_LOG.md` — 新增 v2.2 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v2.2

## v2.1 — 2026-03-29

### 變更內容
- 評估精靈頁面 Storytelling 重構：四步驟改為章節式旅程（認識您的家 / 了解房屋狀況 / 建立帳號 / 選擇方案）
- 每個步驟加入情感副標題、裝飾 emoji、底部溫暖提示（.warm-note）
- 面板視覺升級：大號淡化步驟序號（120px serif, 5% opacity）、頂部 4px 金色漸層線
- 新增 --border-default: #e6e6e6 token，所有表單 input 和卡片邊框統一使用
- Spring 動畫統一為 1.2s duration，新增面板切換 blur 轉場動畫（panel-enter / panel-exit）
- 進度條步驟標籤改為章節名稱（認識您的家、了解房屋狀況、建立帳號、選擇方案）
- 瀏覽區建商圖片路徑更新為 new-highrise-1/2/3.png + construction-hero.png
- 送出後提示加入溫暖結語

### 檔案異動
- `demos/usafe-evaluate.html` — 完整重寫，Storytelling wizard 重構
- `DEV_LOG.md` — 新增 v2.1 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v2.1

## v2.0 — 2026-03-29

### 變更內容
- Landing page 全面重新設計，參考 family.co 簡約風格
- Hero：改用靜態圖片 (cover.png) + 左對齊文字佈局 + 直式 Logo
- 新增品牌金色 (#FFB200) Marquee 跑馬燈
- 案例區：3-column 卡片設計，含 Urban Renewal 實景圖、tag 徽章、案件統計
- 統計區：2x2 簡潔卡片（移除側邊圖片）
- 服務流程：改為垂直 Timeline 佈局（避免連線對齊問題）
- 信任區：改為無限水平捲動卡片（含左右漸層遮罩）
- 新增 FAQ 手風琴區塊（5 題都更常見問題）
- 新增獨立 CTA 區塊（連結至 usafe-evaluate.html）
- 所有元素使用 Spring 動畫曲線 + IntersectionObserver 觸發
- 移除 Netflix 瀏覽區與多步驟精靈（已獨立至 evaluate 頁面）

### 檔案異動
- `demos/usafe-landing-v2.0.html` — 新建，Landing page v2.0 全面重新設計
- `DEV_LOG.md` — 新增 v2.0 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v2.0

## v1.7 — 2026-03-29

### 變更內容
- 新建獨立免費評估精靈頁面（usafe-evaluate.html）
- 四步驟 Wizard：基本資訊 → 房屋細節 → 登入/註冊 → 選擇方案
- 進度指示器：active = gold 邊框光暈、done = teal 打勾、連線 = icon-design 色
- 三階方案卡片：免費（$0）/ 進階推薦（icon-design badge）/ VIP
- Netflix 風格建商瀏覽區（登入後顯示）：精選建商 + 熱門都更方案橫向捲動
- 固定 pill nav（白灰毛玻璃）含「回首頁」連結
- 響應式：960px 方案卡 1-col、640px 表單 1-col + 步驟標籤隱藏

### 檔案異動
- `demos/usafe-evaluate.html` — 新建，獨立評估精靈頁面
- `DEV_LOG.md` — 新增 v1.7 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v1.7、Sidebar 新增「免費評估精靈」連結、新增 r-evaluate 頁面

## v1.6 — 2026-03-29
### 變更內容
- Hero overlay 減輕（0.35/0.25），文字加 text-shadow 維持可讀性
- 步驟徽章顏色從 teal 改為 icon-design (#f24822)，加陰影
- 步驟連線修正為居中對齊，步驟描述加 strong 強調關鍵字
- 新增 Marquee 跑馬燈條（teal 背景，介紹平台服務）
- Stats 區改為左圖右 2x2 卡片佈局，數字改用 gold-bright (#FFB200)
- 案例圖片從 emoji 改為 Urban Renewal 實拍照片（object-fit: cover）
- 新增四步驟評估精靈（Multi-step Wizard）取代原聯絡表單
  - Step 1: 基本資訊 / Step 2: 房屋細節 / Step 3: 登入註冊 / Step 4: 方案選擇
  - 含進度條、步驟指示器、上下步按鈕
  - 方案選擇含三階（免費/進階推薦/VIP）
- 新增 Netflix 風格建商瀏覽區（登入後顯示）
  - 精選建商橫向滾動列 + 熱門都更方案列
  - hover 放大效果、scroll-snap、深色背景
- Hero CTA 連結從 #contact 改為 #evaluate

### 檔案異動
- `demos/usafe-landing-v1.6.html` — 新建，評估精靈 + 建商瀏覽版
- `DEV_LOG.md` — 新增 v1.6 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v1.6

## v1.5 — 2026-03-29
### 變更內容
- Nav bar 改為白灰中性毛玻璃風格（取代深色 Pill Nav）
- 捲動超過 Hero 後 Nav 自動縮窄，帶 spring 彈性動畫（cubic-bezier）
- Hero 漸層減輕：由重黑改為中性暖褐半透明
- Hero 標題改為「讓您的都更案件 更透明、更快速」，強調平台透明定位
- 副標文案改為 50+ 歲友善語氣，強調進度可查、安心守護
- CTA 按鈕改為品牌金（gold.500 #C8A75D），取代磚紅
- 全站重點色引入 Figma token：teal（步驟徽章、eyebrow）、gold（CTA、連線）
- 手機版導航選單改為白色毛玻璃��景

### 檔案異動
- `demos/usafe-landing-v1.5.html` — 新建，中性 Nav + 透明定位版
- `DEV_LOG.md` — 新增 v1.5 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v1.5

## v1.4 — 2026-03-29
### 變更內容
- Superpower.com 深度還原風格：深色 Pill 形狀懸浮 Nav
- Hero 全螢幕暗色影片背景，文字靠左下對齊
- 保留 v1.1 文案（「三代人的根 / 不該被遺忘」）
- 單一磚紅 CTA 按鈕（移除第二顆按鈕）
- Logo 改用 base64 內嵌（解決 computer:// 路徑失效問題）
- 影片路徑修正為 assets/videos/cover.mp4
- Nav 精簡為 3 個連結 + 1 登入按鈕
- 白色 Stats 卡片區（Superpower 風格）
- 橘色數字步驟徽章 + 漸層連線
- 聯絡表單左右兩欄布局

### 檔案異動
- `demos/usafe-landing-v1.4.html` — 新建，Superpower 深度還原版
- `U-SAFE_設計文件.html` — 版本表新增 v1.4
- `DEV_LOG.md` — 新增 v1.4 紀錄

## v1.3 — 2026-03-29
### 變更內容
- 全新 Landing Page，參考 Superpower.com 風格重構
- 整合產品規格文件 v1.0 內容：三階段會員成長路徑（免費→高級→媒合）
- 新增 AI 功能展示區（交替圖文排版）：風險快篩、情境模擬+家族溝通、建商匹配+合約解讀
- 新增會員三階卡片（含功能列表、CTA 按鈕、推薦標籤）
- 新增 Dark CTA 區塊（用戶心理變化路徑）
- 新增品牌引言區塊（Superpower-style center quote）
- Hero 文案更新：「從理解到行動，AI 陪你走每一步」
- 導航改為透明→捲動後毛玻璃（Superpower 風格）
- 按鈕系統統一：btn-primary（磚紅圓角）+ btn-secondary（描邊圓角）
- 影片路徑更新為 cover.mp4（用戶已替換檔案格式）

### 檔案異動
- `demos/usafe-landing-v1.3.html` — 新建，Superpower 風格 Landing Page
- `DEV_LOG.md` — 新增 v1.3 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v1.3 + r-landing 說明更新

## v1.2 — 2026-03-29
### 變更內容
- Landing Page 色調從暗色電影風轉換為溫柔明亮風（Warm Light）
- CSS 變數全面對齊 Figma Design Token Light 模式（bg #F8F5EA 暖米色）
- Modal 背景改為白色，表單輸入改為暖色調
- CTA 按鈕文字改為白色（磚紅底白字）
- Logo 改用 logo-dark.png（深色書法體，適配淺色背景）
- 手機版導航選單改為暖色毛玻璃背景
- cover.mov 轉檔為 hero-video.mp4（H.264），確保跨瀏覽器相容
- 影片源順序調整：mp4 優先、mov 備援

### 檔案異動
- `demos/usafe-landing-v1.1.html` — 全面色調轉換 + 影片路徑修復
- `assets/videos/hero-video.mp4` — 新增，由 cover.mov 轉檔產生
- `DEV_LOG.md` — 新增 v1.2 紀錄
- `U-SAFE_設計文件.html` — 版本表新增 v1.2

## v1.1 — 2026-03-29
### 變更內容
- Landing Page 升級為電影感風格（Cinematic Hero）
- 新增液態玻璃（Liquid Glass）視覺效果
- 新增膠片顆粒（Film Grain）動畫覆蓋層
- 新增 fade-rise 與 scroll fade-up 動畫
- 全螢幕影片背景（cover.mov）

### 檔案異動
- `demos/usafe-landing-v1.1.html` — 新建，電影感 Landing Page

## v1.0 — 2026-03-29
### 變更內容
- 新建登入前 Landing Page（信任導向），完整版包含六大區塊
- 品牌色系以 Figma 最新為準（bg-brand #FFB200、bg #F8F5EA）
- 建立 CLAUDE.md 專案開發規則（含設計文件同步規則）

### 檔案異動
- `demos/usafe-landing-v1.0.html` — 新建，登入前 Landing Page 完整版
- `CLAUDE.md` — 新建，專案開發規則與設計文件同步指引
- `U-SAFE_設計文件.html` — 新增 r-landing 頁面說明 + 版本表 v1.0 + Sidebar 連結
