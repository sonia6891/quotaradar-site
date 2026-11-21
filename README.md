# 額度雷達 QuotaRadar 官網

額度雷達（QuotaRadar）App 的介紹網頁，預計用 GitHub Pages 公開在 https://quotaradar.pocketjoystudio.com/ （`CNAME` 檔不要刪；pocketjoystudio.com 是工作室共用網域，這裡只用 quotaradar 子網域）。這個 repo 只有網頁檔案（HTML、CSS、圖片），沒有 App 的程式。App 本身在 `D:\dev\ai-quota`。

| 網址 | 內容 |
|---|---|
| `/` | 繁體中文（第一次來會照瀏覽器語言轉到簡中、英文、日文或韓文版） |
| `/zh-hans/` | 简体中文 |
| `/en/` | English |
| `/ja/` | 日本語 |
| `/ko/` | 한국어 |
| `/privacy/` | 隱私權政策（中英對照） |
| `/support/` | 支援與常見問題（中英對照） |

- 樣式都在 `assets/style.css`；沒有外部字型、沒有追蹤碼、不需要 build。
- 截圖（`assets/shots/`）、首屏手機圖（`assets/img/hero-*.jpg`）來自 App repo 的 `store/screenshots/ios/`（各語言子資料夾），縮成 540 寬 JPEG。分享預覽圖是 `assets/img/og-*.jpg`（1200×630）。
- 隱私權政策、支援頁是從 App repo 的 `site/privacy/index.html`、`site/support/index.html` 原文照搬（只多加 favicon）。App 改了政策，要把新的檔案複製過來，不要自己改字。
- 舊網址 → 新網址：
  - https://sonia6891.github.io/quotaradar-app/ → https://quotaradar.pocketjoystudio.com/
  - https://sonia6891.github.io/quotaradar-app/privacy/ → https://quotaradar.pocketjoystudio.com/privacy/
  - https://sonia6891.github.io/quotaradar-app/support/ → https://quotaradar.pocketjoystudio.com/support/
  - App 裡的隱私權政策連結（`src/core/purchases.ts` 的 `PRIVACY_URL`）還指向舊網址；換網址時 App 和 App Store Connect 的隱私權政策／支援網址要一起改。

## 數字從哪裡來（App 改了，這裡要一起改）

| 網頁上的數字 | 來源（`D:\dev\ai-quota`） |
|---|---|
| 完整版 NT$199（只寫在繁中版；其他語言只寫「一次買斷」） | `store/listing.md:10`、`src/app/paywall.tsx:25` |
| 免費版最多 3 家 AI | `src/core/gating.ts:15`（`FREE_AI_LIMIT`）、`src/i18n.ts:345` |
| 完整版免費試用 3 天 | `src/core/gating.ts:11`（`TRIAL_DAYS`） |
| 剩 20%、5% 時通知 | `src/core/forecast.ts:106`（`LOW_LEVELS`）、`store/listing.md:55` |
| 7 天統計 | `store/listing.md:69`、`src/i18n.ts:343` |
| 三種外觀主題 | `store/listing.md:72-73` |
| 支援的 AI（12 家，β 是測試中） | `src/core/providers/index.ts`（`beta: true` 的是 β） |
| App Store ID 6836609602 | `config/brand.json` |

免費版 3 家、3 天試用是 1.0.2（2026-11-21 `be6e3e9`）才有的；1.0.1 的免費版不限家數。

## 上架、改版時要改的地方

- **Google Play 上架後**：五個 `index.html` 裡兩個 Google Play 按鈕的 `class="store soon"` 改成 `class="store"`，拿掉 `aria-disabled="true"`、`tabindex="-1"` 和 `<span class="tag">…</span>`；下載區那句「Android 版即將上架」也要改。
- App Store 按鈕：繁中連台灣商店、英文連美國商店，簡中／日文／韓文用 `https://apps.apple.com/app/id6836609602`（會自己轉到使用者所在地區）。
- 改價格、免費額度、試用天數、支援的 AI：照上表找到 App 的新數字，五個語言一起改。
