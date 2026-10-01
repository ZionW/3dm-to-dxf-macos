# 3DM → DXF：Windows 版

[English](README.Windows.en.md) · [GitHub](https://github.com/ZionW/3dm-to-dxf-macos)

適用 Windows 10 / 11 的 Intel 或 AMD 64 位元電腦。下載 `3DM-to-DXF-Windows-x64-v0.10.0.zip`，先解壓縮整個資料夾，再將單一或多個 `.3dm` 檔案拖到 `3DM to DXF.exe` 圖示。也可以建立 EXE 的桌面捷徑，再把檔案拖到捷徑。

程式沒有主視窗，不會啟動 Rhino，也不需要安裝 Python、Rhino 或 ODA。DXF 會輸出到原檔資料夾，保留原檔名；同名已存在時自動使用 `_1`、`_2`。成功或失敗透過 Windows 通知提示。Windows 的勿擾模式或通知設定可能隱藏提示；批次結果同時記錄於 `%LOCALAPPDATA%\3DM-to-DXF\logs`。不要以系統管理員身分執行，否則 Explorer 拖曳可能被 Windows 阻擋。

這個版本未購買 Windows 程式碼簽章憑證，首次執行可能出現 SmartScreen 發行者提示。請確認下載來源是本專案的 GitHub Release，並核對下載頁的 SHA-256。

支援常見點、線、圓、圓弧、折線、NURBS、網格、填色、文字、可表達的區塊參照、線性尺寸與平面參考圖片，保留圖層名稱、顏色、可見性、鎖定及單位。寫入後會回讀 DXF，核對來源物件 ID、物件類型與填色邊界數量；DXF audit 若需要修復，則停止輸出。

一般 Brep 實體、特殊物件或不支援的變換可能無法轉檔。此時會在來源檔旁產生 `.conversion-error.txt`，同一批其他檔案仍會繼續。成功後會附上 `.dxf.verification.json`。字型顯示取決於接收端安裝的字型；圖片是外部參照，移動 DXF 時要一起移動 `<原檔名>_embedded_files` 資料夾。來源隱藏的圖層會保持隱藏。

已在 GitHub Windows runner 驗證打包 EXE 的中文／日文含空白路徑、填色內圈、區塊位置、尺寸、NURBS、網格、圖層、DXF 回讀、同名檔保護及混合成功／失敗批次。Explorer 拖曳手勢與通知實際顯示仍需在 Windows 桌面實測。

轉檔完全在本機執行，不會上傳模型。

## 從原始碼建置

安裝 Python 3.14 x64、Git、CMake 及 Visual Studio 2022 Build Tools（C++ 桌面開發）。在解壓縮的原始碼目錄執行 PowerShell：

```powershell
./build.ps1
```

建置會下載固定 commit 的官方 openNURBS，以及 `requirements.txt` 指定版本的 PyPI 套件。產物放在 `release`，測試通過才會打包。原始碼提供供檢視與自行建置；第三方元件授權文字隨下載包附上。
