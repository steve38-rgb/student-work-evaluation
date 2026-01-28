# 學生作品評量網站部署指南

本專案包含一個基於 React + Tailwind 的前端網站，以及一個 Google Apps Script (GAS) 後端腳本。

## 📁 檔案結構
- `index.html`: 首頁（學生提交作品）
- `comments.html`: 評語查詢頁
- `admin.html`: 教師管理頁入口
- `js/config.js`: 設定檔
- `Code.gs`: 後端程式碼 (Google Apps Script)

## ✅ 功能測試
1. **提交作品**: 在首頁輸入姓名與內容，點選提交。確認顯示「已收到...」。
2. **查看 Sheet**: 確認 Google Sheet 中新增了一筆資料，且包含 AI 生成的評語。
3. **查詢評語**:前往 `comments.html`，輸入姓名，確認能看到剛剛的評語卡片。

## 🔒 安全性說明
- Gemini API Key 已封裝於 GAS 後端，前端只透過 GAS URL 存取，確保安全性。


