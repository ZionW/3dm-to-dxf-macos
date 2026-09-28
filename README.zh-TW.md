# 3DM → DXF：macOS 使用說明

[English](README.en.md) · [首頁](README.md)

## 安裝與使用

1. 從 [Releases](../../releases/latest) 下載 `3DM-to-DXF-macOS-arm64-v0.9.zip`，解壓縮取得 `3DM to DXF.app`。
2. 把單一或多個 `.3dm` 檔拖到 App 圖示上。
3. App 在原檔資料夾產生同名 `.dxf`。若已存在，會依序使用 `_1.dxf`、`_2.dxf`，不覆蓋舊檔。完成或失敗會顯示 macOS 通知。

App 不顯示主視窗，也不啟動 Rhino。它直接寫入 DXF，不需要 DWG 轉檔工具或 ODA。

## 系統需求

- Apple Silicon Mac；App 設定的最低版本為 macOS 13。本版在 macOS 27.2 實測，其他版本尚未實測。
- App 使用本機臨時簽章，尚未經 Apple 公證。若 macOS 阻擋第一次開啟，可在 Finder 對 App 按右鍵選「打開」，依系統指示繼續。

## 轉換範圍與限制

支援常見點、線、圓弧、圓、Polyline、NURBS 曲線、部分網格、填色、文字、可表示的區塊參照與尺寸，以及平面參考圖片。保留圖層名稱、顏色、隱藏狀態與圖面單位。輸出後會重新讀取 DXF，核對來源物件及填色數量；不能安全轉換的物件會使該檔失敗並在原檔旁寫入 `.conversion-error.txt`。

這不是完整的 Rhino 匯出器。一般 Brep 實體、特殊材質與其他未支援物件可能無法轉換。文字外觀取決於接收端安裝的字型。原檔中隱藏的圖層會保持隱藏，可在 CAD 的圖層管理員中開啟。

圖片以外部參照儲存。搬移 DXF 時，請同時搬移旁邊的 `<原檔名>_embedded_files` 圖片資料夾。每個成功轉換的 DXF 旁也會產生 `.dxf.verification.json` 核對報告。

## 隱私

轉檔在本機進行；App 不會把 3DM 或 DXF 上傳到網路。這個 GitHub 儲存庫的發行檔只包含 App，不包含使用者模型。
