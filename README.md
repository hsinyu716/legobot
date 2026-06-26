# TTRA 機器人實作檢定一級・學科 線上測驗

依據《學科題庫公告》整理的 **300 題** 學科題庫，做成可直接部署到 **GitHub Pages** 的線上測驗網頁。每次作答會從 300 題中**隨機抽出 20 題**。

## 線上試做

部署到 GitHub Pages 後，網址會是：

```
https://<你的帳號>.github.io/<儲存庫名稱>/
```

## 功能

- 📚 完整 300 題題庫（題目、選項、答案皆以原公告 PDF 影像呈現，含程式積木、齒輪、槓桿等圖示）
- 🎲 每次隨機抽 20 題；同一個瀏覽分頁（session）內**盡量不重複出題**，全部出過一輪後才重新循環
- 🔁 **錯題自動回收**：答對的題目本輪內不再重複；**答錯或未作答的題目會放回題庫**，之後仍會再出現以便複習
- ✅ 交卷後立即評分，逐題標示正確／錯誤並顯示正解
- 📊 **學習統計**：累計作答題次、答對／答錯次數、正確率、已出現題數、曾答錯題數（記錄在瀏覽器 localStorage，可一鍵清除）
- ⚠️ **錯題標記**：過去答錯過的題目會在卡片標上「曾答錯 N 次」，並顯示該題累計答對/答錯次數
- 🔍 題目圖片可點擊放大（lightbox），再點一下二段放大看細節
- 📱 支援手機 / 平板 / 桌機（RWD）
- 🔌 純靜態網頁（HTML/CSS/JS），無需後端、無需建置

## 檔案結構

```
ttra-quiz/
├── index.html        # 測驗網頁（開啟即用）
├── questions.json    # 300 題題庫資料（題號、圖片、選項、答案）
├── corrections.md    # 對參考答案的勘誤與修正紀錄
├── img/              # 每一題的題目影像 q1.png ~ q300.png
└── README.md
```

## 部署到 GitHub Pages

1. 建立一個新的 GitHub 儲存庫，把 `ttra-quiz/` 內所有檔案（含 `img/` 資料夾）上傳。
   > 建議直接把這些檔案放在儲存庫**根目錄**，或放在 `docs/` 資料夾。
2. 進入儲存庫 **Settings → Pages**。
3. **Source** 選擇 `Deploy from a branch`，Branch 選 `main`（資料夾選 `/ (root)` 或 `/docs`）。
4. 儲存後等待約 1 分鐘，即可用上方網址開啟測驗。

## 本機預覽

因為網頁會以 `fetch()` 載入 `questions.json`，直接用瀏覽器開啟 `index.html`（`file://`）可能被瀏覽器安全限制擋下。請改用本機伺服器：

```bash
cd ttra-quiz
python3 -m http.server 8000
# 開啟 http://localhost:8000
```

## 答案來源與勘誤

- 題庫內容取自《學科題庫公告》PDF（共 300 題）。
- 參考答案以 [waterball_453/cursor_ttra.md](https://github.com/hsinyu716/waterball_453/blob/main/cursor_ttra.md) 為基礎。
- 已逐題人工複核，修正其中的錯誤，所有變動詳列於 [`corrections.md`](corrections.md)。
