# site-zhudong-kg：竹東知識圖譜

<!-- hero --><p align="center"><img src="docs/assets/hero.png" alt="site-zhudong-kg" width="860"></p>

以 Google Sheets 當 CMS、React 加 D3 力導向圖呈現的竹東知識圖譜視覺化網站。

## 狀態

- 可運作：前端讀取 GitHub 上的 `graph.json`，由 Google Apps Script 驗證並同步。
- 待辦：地圖模式（Map Mode）、手機版操作優化、統計儀表板。
- 部署：GitHub Pages，網址 https://scott-lbx.github.io/site-zhudong-kg/ （repo 原名 Zhudong，已更名）。

## 快速開始

```bash
npm install
npm run dev       # 開發伺服器
npm run build     # 建置到 dist/
npm run deploy    # 建置並以 gh-pages 發佈 dist/
```

資料更新：在 Google Sheet 編輯 `nodes_*`、`link_*` 工作表，Apps Script（`appscript/Graph.gs`）會驗證並輸出 JSON，沒有本機資料指令。

## 目錄

| 路徑 | 內容 |
|---|---|
| `src/` | React 前端（圖譜、資訊卡、搜尋、時間軸、資料 context） |
| `appscript/` | Google Apps Script（`Graph.gs`、`Image.gs`）與 Token 設定、使用者說明 |
| `docs/` | `使用者操作手冊.md`、`開發技術文件.md` |
| `public/` | 靜態資源 |
| `vite.config.js` | Vite 設定 |

## 主要功能

- D3 力導向圖，時間軸滑桿過濾年份；未設年份的節點視為永久存在。
- 搜尋聚焦、互動圖例、資訊卡（多來源 Info 合併）、工具列自動隱藏。
- Apps Script 自動掃描所有 `nodes_*` 與 `link_*` 工作表：Group 衝突標紅，Link 用到未定義節點則標黃。
- 開發除錯元件 `FilteredGraphLogger`。

詳細的工作表欄位、驗證顏色與部署方式見 `docs/`。

## 相關 repo

- [site-nanao-kg](https://github.com/scott-lbx/site-nanao-kg)：南澳知識圖譜。與本 repo 共用同一套架構（Google Sheets 當 CMS、React、D3 知識圖譜），差別在案場與資料。

## 授權

README 原宣告 MIT License，但 repo 內沒有 LICENSE 檔，授權以未指定處理。
