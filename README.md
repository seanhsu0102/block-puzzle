# 🧱 SEANLAB.net - Block Puzzle Master (積木拼圖大師)

這是一個基於 **Cloudflare Workers** 部署的現代、精美且互動性極佳的 **積木拼圖遊戲 (Block Puzzle Master)**。專為全年齡段（特別是 4-12 歲兒童與拼圖愛好者）設計，具備流暢的拖放體驗、豐富的遊戲模式與難度，以及全球即時積分排行榜！

---

## ✨ 遊戲特色

*   **🎮 經典且流暢的玩法**：支援各種直覺的積木拖放，滿行或滿列即可消除得分，體驗極具爽快感。
*   **📐 多種棋盤尺寸**：
    *   **5x5 (快速挑戰)**：節奏快速，適合短時間休閒。
    *   **9x9 (經典模式)**：標準難度，考驗全局策略。
    *   **12x12 (大師挑戰)**：超大版面，適合高端硬核玩家。
*   **⏱️ 雙重遊戲模式**：
    *   **無盡模式 (Infinite)**：無時間壓力，專注於突破個人最高紀錄。
    *   **時間限時模式 (Timed Challenge)**：5 分鐘限時挑戰，在倒數計時中考驗反應速度。
*   **⚙️ 三段難度調整**：
    *   **簡單 (Easy)**：產生更多易於放置的基礎積木碎片，非常適合兒童遊玩。
    *   **經典 (Classic)**：標準的積木組合與難度。
    *   **困難 (Hard)**：隨機出現挑戰性的極限積木，考驗高手極限。
*   **🏆 全球即時排行榜**：
    *   結合 Cloudflare Workers KV 儲存，實現跨裝置、跨地區的即時前 10 名排行榜。
    *   分門別類記錄不同尺寸、不同模式的排行榜。
*   **🎨 精緻視覺設計**：
    *   採用現代感暗色調與極具質感的漸層色彩搭配。
    *   細緻的微互動動畫與流暢的物理彈性回饋。
    *   送出分數後自動重開局，遊玩體驗無縫接軌。

---

## 📂 專案結構

```text
├── block.html         # 遊戲主網頁 (包含所有的 HTML, CSS 與前端邏輯)
├── package.json       # 專案相依性與指令設定
├── wrangler.toml      # Cloudflare Workers 與 KV 命名空間設定檔
├── scripts/
│   └── build.js       # 建置腳本 (自動將 block.html 封裝進 Worker 入口點)
└── src/
    └── index.js       # 自動產生的 Worker 執行檔 (請勿直接修改此檔案)
```

---

## 🛠️ 開發與建置指引

本專案將前端頁面與後端 API 融合於單一 Cloudflare Worker 中。在每次修改前端網頁 `block.html` 後，需透過建置腳本將其編譯入 `src/index.js` 中。

### 1. 安裝相依套件

在專案目錄下執行：
```bash
npm install
```

### 2. 本地開發與偵錯

啟動本地開發伺服器（會自動進行 build 並啟動本地 Wrangler 模擬 Worker 環境）：
```bash
npm run dev
```
啟動後可在瀏覽器開啟 `http://localhost:8787` 進行遊玩與測試。

### 3. 編譯封裝

手動將 `block.html` 打包進 `src/index.js`：
```bash
npm run build
```

---

## 🚀 部署至 Cloudflare Workers

在部署前，請確保您已安裝 `wrangler` 並登入 Cloudflare 帳戶。

### 1. 建立 KV 命名空間（若尚未建立）

在 Cloudflare 執行以下指令建立排行榜所用的 KV：
```bash
npx wrangler kv:namespace create LEADERBOARD_KV
```
並將輸出的 `id` 更新至 `wrangler.toml` 中的 `id` 欄位。

### 2. 一鍵發佈部署

執行以下指令，系統會自動編譯專案並發佈至 Cloudflare 的全球邊緣網路上：
```bash
npm run deploy
```

---

## 📝 技術與框架說明

*   **前端核心**：純原生 HTML5 / CSS3 / ES6 JavaScript，無額外肥大框架，保證極致的載入速度。
*   **後端儲存**：Cloudflare Workers / Cloudflare KV，提供無伺服器 (Serverless) 高速讀寫。
*   **排版與適應性**：全面支援響應式設計 (RWD)，在手機、平板與桌機上均能完美滿版呈現。

---

## 🤝 貢獻與開發

歡迎提交 Issue 與 Pull Request 來共同改進這個遊戲！您可以隨時調整難度係數、增加新的積木形狀、或美化 UI 動畫。

*Created with ❤️ by SEANLAB.net*
