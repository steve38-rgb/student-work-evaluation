# 學生作品評量網站部署指南

本專案包含一個基於 React + Tailwind 的前端網站，以及一個 Google Apps Script (GAS) 後端腳本。

## 📁 檔案結構
- `index.html`: 首頁（學生提交作品）
- `comments.html`: 評語查詢頁
- `admin.html`: 教師管理頁入口
- `js/config.js`: 設定檔
- `Code.gs`: 後端程式碼 (Google Apps Script)

## 🚀 部署步驟

### 第一步：設定 Google Backend (GAS)
1. 前往 [Google Drive](https://drive.google.com/) 建立一個新的 Google Sheet。
   - **Sheet ID**: 請確認網址中的 ID 是否為 `13CI6qJI8mDpEpMqV5wjxgzvG2u0jCysdkKxu2nYk5oI` (或修改 `Code.gs` 中的 `SHEET_ID` 為您的新表格 ID)。
   - **欄位設定**: 第一列請依序填入：`時間`, `姓名`, `作品內容`, `四字評語`, `文字回饋`。

2. 在 Sheet 中點選 `擴充功能` > `Apps Script`。

3. 將本專案中的 `Code.gs` 內容複製並貼上到 Apps Script 编辑器中，覆蓋原有內容。

4. 點選右上角 `部署` > `新增部署作業`。
   - **類型**: 選取「網頁應用程式」。
   - **說明**: 填寫「Initial Deploy」。
   - **執行身分**: **我 (Me)**。
   - **誰可以存取**: **任何人 (Anyone)** (這很重要，否則前端無法呼叫)。
   
5. 點選 `部署`，並授權存取權限。

6. 複製產生的 **網頁應用程式網址 (Web App URL)**。

### 第二步：連接前端
1. 開啟 `site/js/config.js` 檔案。
2. 將 `GAS_API_URL` 的值替換為您剛剛複製的網址。

### 第三步：啟動網站
由於本網站使用靜態 HTML 架構，您可以透過以下方式啟動：
- **本地測試**: 直接用瀏覽器開啟 `index.html`。
- **正式部署**: 將 `site` 資料夾中的所有檔案上傳至 GitHub Pages, Netlify, 或 Vercel。

## ✅ 功能測試
1. **提交作品**: 在首頁輸入姓名與內容，點選提交。確認顯示「已收到...」。
2. **查看 Sheet**: 確認 Google Sheet 中新增了一筆資料，且包含 AI 生成的評語。
3. **查詢評語**:前往 `comments.html`，輸入姓名，確認能看到剛剛的評語卡片。

## 🔒 安全性說明
- Gemini API Key 已封裝於 GAS 後端，前端只透過 GAS URL 存取，確保安全性。
