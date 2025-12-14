# Threads Image Fixer (CORP Patch) - Threads 圖片破圖修復插件

這是一個開源的 Chrome 擴充功能，專門用於解決 **Threads (threads.net)** 網頁版瀏覽時，圖片因 `Cross-Origin-Resource-Policy (CORP)` 限制而導致的破圖問題 (`net::ERR_BLOCKED_BY_RESPONSE.NotSameOrigin`)。

## ⚠️ 問題背景

當你在瀏覽器上瀏覽 Threads 時，Meta 的圖片 CDN (如 `fbcdn.net`, `cdninstagram.com`) 有時會回傳嚴格的安全性表頭：

- `Cross-Origin-Resource-Policy: same-origin`

這告訴瀏覽器：「只有同源（Same-Origin）的網站可以讀取這張圖片」。由於 `threads.net` 與圖片 CDN `fbcdn.net` 不同源，瀏覽器會依照規範阻擋圖片渲染，導致使用者看到破圖。

本插件透過 Chrome Extension Manifest V3 標準，動態移除這些限制表頭，讓圖片恢復正常顯示。

## 📂 專案檔案結構

確保您的資料夾中包含以下檔案：

- `manifest.json` (插件核心設定檔)
- `rules.json` (攔截與修改規則)
- `README.md` (本說明文件)
- `icons/` (插件圖示資料夾)

## 🚀 安裝說明

由於本插件尚未上架至 Chrome Web Store，請依照以下步驟手動安裝（Developer Mode）：

1. **下載與解壓縮**
   - 前往本頁面右側的 **Releases** 區塊。
   - 下載最新的 `.zip` 壓縮檔。
   - **請務必解壓縮檔案**：將壓縮檔解壓至您習慣的位置（例如桌面）。
   - *檢查*：確認解壓後的資料夾內含有 `icons/` 資料夾與 `manifest.json` 檔案。

2. **開啟擴充功能管理頁面**
   - 在 Chrome 網址列輸入：`chrome://extensions/`
   - 或者點擊右上角選單 > 擴充功能 > 管理擴充功能。

3. **開啟開發人員模式**
   - 在頁面右上角，將 **「開發人員模式」 (Developer mode)** 的開關打開。

4. **載入未封裝項目**
   - 點擊左上角的 **「載入未封裝項目」 (Load unpacked)** 按鈕。
   - 選擇步驟 1 的資料夾。

5. **重新整理 Threads**
   - 回到 Threads 頁面，按 `Ctrl+F5` (Windows) 或 `Cmd+Shift+R` (Mac) 強制重新整理，圖片應可正常顯示。

## 🛠 技術原理 (Interception Mechanism)

本插件使用 Google Chrome 最新的 **Manifest V3** 規範，並利用 **`declarativeNetRequest` API** 來處理網路請求。

### 1. 宣告式網路請求 (DNR)
與舊版 V2 的 `webRequest` 不同，本插件**不會**透過 JavaScript 讀取或監聽每一個封包的內容（這樣太慢且不安全）。我們只是向瀏覽器註冊一份 `rules.json` 規則清單，由瀏覽器底層直接執行。

### 2. Header 修改邏輯
當瀏覽器發出的請求網址符合 Meta CDN 的特徵（正則表達式匹配）時，瀏覽器會自動執行以下動作：

- **移除限制性表頭**：
  - `Cross-Origin-Resource-Policy` (移除 same-origin 限制)
  - `Cross-Origin-Opener-Policy`
  - `Cross-Origin-Embedder-Policy`
- **加入允許表頭**：
  - `Access-Control-Allow-Origin: *` (允許跨域讀取)

### 3. 匹配規則 (Regex Filter)
為了涵蓋所有動態生成的 CDN 子網域（如 `instagram.fkhh1-1.fna.fbcdn.net`），我們使用正則表達式進行廣泛匹配：
- `.*fbcdn\\.net.*`
- `.*cdninstagram\\.com.*`

## 🔒 安全與隱私聲明 (Security & Privacy)

我們深知使用者對於瀏覽器插件權限的擔憂，在此鄭重聲明：

1. **不收集任何數據**：
   本插件沒有後端伺服器，**不會**收集、儲存或傳送您的瀏覽紀錄、Cookies、帳號資訊或任何個人資料。所有的運作都在您的瀏覽器本機端完成。

2. **權限使用說明**：
   - 插件安裝時會提示「讀取及變更您在所有網站上的資料」，這是因為我們使用了 `declarativeNetRequest` 搭配 `<all_urls>` 或廣泛的主機權限來匹配不固定的 CDN 網域。
   - 這是為了修復圖片顯示的必要技術手段，而非為了讀取網頁內容。

3. **開源透明**：
   本專案為完整開源代碼。您隨時可以檢查 `manifest.json` 和 `rules.json` 檔案，確認沒有任何惡意程式碼或追蹤腳本。

## 📝 免責聲明

- 本專案與 Meta Platforms, Inc.、Instagram 或 Threads 無任何官方關聯。
- 本工具僅供技術研究與個人使用，用於修復瀏覽器端的顯示問題。

## License

MIT License