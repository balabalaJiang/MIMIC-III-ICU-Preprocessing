# HW-A2: 分層抽樣對模型表現的影響 (MIMIC3C)

## 專案簡介
本專案為資料探勘與機器學習課程作業（HW-A2）。主要探討「分層抽樣（Stratified Sampling）」在高度不平衡的真實醫療資料中，對於不同資料規模（n=100, 500, 6000）與 7 種分類模型表現及變異程度的實際影響。

## 執行環境與方案說明
* **使用方案**：**方案 B**（為避免繼承 HW1 可能的標籤偏移與維度過高問題，本專案直接從 Kaggle 原始檔 `mimic3c.csv` 重新進行輕量前處理與 One-Hot 編碼，並已嚴格排除 `LOSdays` 等標籤洩漏欄位）。
* **環境依賴**：執行所需套件與確切版本號請參考專案根目錄下的 `requirements.txt`。

## 資料來源與預期路徑
* **原始資料來源**：[Kaggle — MIMIC-III C Clinical Database](https://www.kaggle.com/datasets/drscarlat/mimic3c)
* **預期路徑**：請確保原始資料檔放置於 `data/` 目錄下（即 `data/mimic3c.csv`）。

## 執行步驟
1. 確保已安裝 `requirements.txt` 中所列之 Python 套件環境。
2. 確認 `data/mimic3c.csv` 檔案已放置於正確路徑。
3. 開啟 Jupyter Notebook `A2_1258001.ipynb`。
4. 點擊選單列的 `Kernel` -> `Restart & Run All`。
5. 程式將自動執行完整的 840 次實驗迴圈與統計檢定，所有結果將自動產出至 `output/` 資料夾。

## 預期產出結構 (output/ 目錄)
執行完畢後，`output/` 將自動生成以下檔案：
* `mimic3c_results.csv`: 840 次實驗的完整結果紀錄。
* `significance_full.csv` & `significance_table.md`: Paired t-test 顯著性檢定結果。
* `ceiling_effect_table.md`: 天花板效應評估表 (n=500)。
* `std_ratio_table.md`: 小資料 F1 變異比例表 (n=100)。
* `mimic3c_boxplot_n100.png` 等 3 張: 各資料規模下的分布盒鬚圖。