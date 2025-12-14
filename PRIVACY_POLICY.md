# Privacy Policy / 隱私權政策

**Last Updated / 最後更新日期:** 2025-12-14


## 繁體中文版本

### 1. 簡介
「Threads Image Fixer (CORP Patch)」（以下簡稱「本擴充功能」）是一款旨在修復 Threads 網站因跨來源資源策略（CORP）限制而導致圖片破圖問題的瀏覽器擴充功能。我們非常重視您的隱私，並致力於保護您的權益。

### 2. 資料收集與使用
**我們絕對不會收集、儲存或傳送您的任何個人資料。**

* **不收集個人資訊**：我們不會收集您的姓名、電子郵件、IP 位址或任何可識別個人的資訊。
* **不追蹤瀏覽紀錄**：我們不會追蹤、記錄或傳送您的瀏覽紀錄至任何遠端伺服器。
* **不存取 Cookies**：我們不會存取或儲存您的 Cookies 或工作階段資料。

本擴充功能的所有運作皆完全在您裝置上的瀏覽器內本地執行。

### 3. 權限使用說明
為了正常運作，本擴充功能需要以下特定權限：

* **`declarativeNetRequest` 與 `declarativeNetRequestWithHostAccess`**：這些權限僅用於修改來自 Meta CDN（如 `fbcdn.net`、`cdninstagram.com`）之圖片資源的特定 HTTP 回應表頭（主要是 `Cross-Origin-Resource-Policy`）。這是解決圖片載入錯誤的必要技術手段。
* **主機權限（Host Permissions，如 `<all_urls>` 或特定網域）**：由於 Threads 使用的圖片 CDN 網域是動態且多樣的，本擴充功能需要廣泛的主機權限來匹配這些網址模式並套用修復規則。我們不會利用此權限讀取或修改網頁內容。

### 4. 第三方服務
本擴充功能不使用任何第三方分析工具（如 Google Analytics）或廣告聯播網。

### 5. 開源聲明 (Open Source)
本專案為完全 **開源 (Open Source)** 軟體。
我們相信透明度是信任的基礎。本擴充功能的完整原始碼皆公開可供審閱。您可以隨時前往我們的程式碼儲存庫（GitHub Repository）檢查，確認其中不包含任何惡意程式碼或隱藏的資料收集機制。

### 6. 免責聲明
本擴充功能為非官方工具，與 Meta Platforms, Inc.、Instagram 或 Threads 無任何關聯，亦未獲得其認可或贊助。

### 7. 聯絡我們
如果您對本隱私權政策有任何疑問，請透過我們的 GitHub 儲存庫 Issue 頁面與我們聯繫。

## English Version

### 1. Introduction
"Threads Image Fixer (CORP Patch)" (hereinafter referred to as "the Extension") is a browser extension developed to fix broken image rendering issues on the Threads website caused by Cross-Origin Resource Policy (CORP) restrictions. We respect your privacy and are committed to protecting it.

### 2. Data Collection and Usage
**We do not collect, store, or transmit any of your personal data.**

* **No Personal Information:** We do not collect your name, email address, IP address, or any other personally identifiable information.
* **No Browsing History:** We do not track, record, or send your browsing history to any remote servers.
* **No Cookies:** We do not access or store your cookies or session data.

All operations performed by the Extension occur entirely locally within your browser on your device.

### 3. Permissions Justification
To function correctly, the Extension requires specific permissions:

* **`declarativeNetRequest` & `declarativeNetRequestWithHostAccess`:** These permissions are used solely to modify specific HTTP response headers (specifically `Cross-Origin-Resource-Policy`) for image resources originating from Meta's CDNs (e.g., `fbcdn.net`, `cdninstagram.com`). This is a technical necessity to resolve the image loading errors.
* **Host Permissions (`<all_urls>` or specific domains):** Because the CDN domains used by Threads are dynamic and varied, the Extension requires broad host permissions to match these URL patterns and apply the necessary header fixes. We do not use these permissions to read or modify web page content.

### 4. Third-Party Services
The Extension does not use any third-party analytics tools (e.g., Google Analytics) or advertising networks.

### 5. Open Source Statement
This project is fully **Open Source**.
We believe in transparency. The complete source code of this Extension is available for public audit. You can verify that there is no malicious code or hidden data collection mechanisms by visiting our code repository.

### 6. Disclaimer
This Extension is an unofficial tool and is not affiliated with, endorsed, or sponsored by Meta Platforms, Inc., Instagram, or Threads.

### 7. Contact
If you have any questions regarding this Privacy Policy, please contact us via the issue tracker on our GitHub repository.

---
