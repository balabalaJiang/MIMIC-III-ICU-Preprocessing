# MIMIC-III ICU 臨床資料前處理與特徵工程

## 專案簡介
本專案為 [資料探勘與機器學習] 的作業一。主要目的是針對MIMIC-III C Clinical Database進行資料清理、探索性資料分析(EDA)、缺失值處理以及特徵工程，最終輸出一份可用於機器學習建模的Analysis-Ready Table。

## 資料集來源
* 原始資料來源:請參見[Kaggle — MIMIC-III C Clinical Database (MIMIC3C)](https://www.kaggle.com/datasets/drscarlat/mimic3c)
* 本專案使用資料表:`mimic3c.csv`

## 如何執行本專案
1. 確保您的環境已安裝`requirements.txt`中列出的套件。
2. 請確保Kaggle下載的原始資料檔`mimic3c.csv`放置於`data/`目錄下(即`data/mimic3c.csv`)。若需批改時，請維持`data/`目錄存在。
3. 開啟Jupyter Notebook`A1_1258001.ipynb`。
4. 點擊選單列的`Kernel` -> `Restart & Run All`。
5. 程式將會自動由上往下執行，並在`output/`目錄中生成所需的結果檔案。

## 目錄結構與預期輸出
* `data/mimic3c.csv`：原始資料(需自行下載放置)。
* `output/df_model_ready.csv`：程式自動生成的最終特徵矩陣(Analysis-Ready Table)。
* `output/eda_key_stats.csv`：程式自動生成的EDA重點統計表。
* `A1_1258001.md`：包含分析結果與說明的完整文字報告。