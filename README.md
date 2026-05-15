# MIMIC-III 醫療資料探勘實務：從資料前處理到抽樣策略實證

**課程名稱**：資料探勘與機器學習

---

## 專案簡介
本專案基於 MIMIC-III C Clinical Database 醫療資料集，旨在開發一個臨床死亡風險預測框架。專案依據資料處理與建模流程，分為兩個獨立且連續的核心子專案：

* **第一階段：A1_Data_Preprocessing (資料前處理與 EDA)** 針對原始臨床數據進行數據清洗、缺失值處理、特徵工程與探索性資料分析（EDA），排除標籤洩漏特徵，並產出可供建模的乾淨資料集。
* **第二階段：A2_Machine_Learning (抽樣策略與模型穩定性實證)** 探討分層抽樣（Stratified Sampling）在高度不平衡（9:1）且不同資料規模（n=100, 500, 6000）下，對 7 種分類模型（包含傳統機器學習與神經網路）預測表現與變異程度的影響。

---

## 專案目錄結構
```text
MIMIC-III-Project/
├─ .gitignore                 # 版本控制忽略清單 (阻擋 .csv 等大型與暫存檔)
├─ README.md                  # 專案總說明檔
├─ requirements.txt           # 專案總套件與環境依賴清單
│
├─ A1_Data_Preprocessing/     # 第一階段：資料理解與前處理
│  ├─ A1_1258001.ipynb        # EDA 與前處理主程式碼
│  ├─ A1_1258001.md           # 第一階段技術報告
│  ├─ PROMPT_LOG.md           # A1 的 AI 協作提示詞紀錄
│  ├─ DEBUG_LOG.md            # A1 的實驗除錯紀錄
│  ├─ data/
│  └─ output/                 # A1 產出的 df_model_ready.csv 等
│
└─ A2_Machine_Learning/       # 第二階段：機器學習建模與統計檢定
   ├─ A2_1258001.ipynb        # 核心實驗與訓練迴圈主程式碼
   ├─ A2_1258001.md           # 第二階段實證研究報告
   ├─ PROMPT_LOG.md           # A2 的 AI 協作提示詞紀錄
   ├─ DEBUG_LOG.md            # A2 的實驗除錯紀錄
   ├─ data/
   └─ output/                 # A2 產出的視覺化圖表與 Markdown 結果表格
```

# MIMIC-III 醫療資料探勘實務：從資料前處理到抽樣策略實證

## 環境建置與執行方法

### 1. 環境安裝
建議使用 Python 3.10+ 環境。請在根目錄（MIMIC-III-Project/）下開啟終端機並執行：

```bash
pip install -r requirements.txt
```

### 2. 資料集準備
本專案的原始資料集為 Kaggle 上的 `mimic3c.csv`。請自行下載並確認 Notebook 內的讀取路徑是否與您存放檔案的位置一致（預設為存放於各自階段的 `data/` 資料夾內或依 Notebook 內路徑設定）。

### 3. 執行實驗
*   **執行第一階段 (A1)**：切換至 `A1_Data_Preprocessing` 目錄，使用 Jupyter Notebook 開啟 `A1_1258001.ipynb`，點擊 **Restart & Run All**。
*   **執行第二階段 (A2)**：切換至 `A2_Machine_Learning` 目錄，使用 Jupyter Notebook 開啟 `A2_1258001.ipynb`，點擊 **Restart & Run All**。所有統計結果與圖表將自動匯出至 `A2_Machine_Learning/output/` 目錄中。

---

## 核心發現總結

*   **標籤洩漏防範**：在醫療預測任務中，嚴格遵循臨床資訊取得的時序性至關重要，必須剔除 `LOSdays` 等事後方可知曉的欄位以反映真實預測力。
*   **抽樣策略的侷限**：在 MIMIC-III 此類高雜訊的真實電子病歷資料中，分層抽樣（Stratified Sampling）雖在極小樣本中具備微弱的穩定作用，但整體並未帶來顯著的效能提升。
*   **天花板效應與模型穩定度**：剝除了高準確率（天花板效應）的掩飾後，MLP 神經網路在面對不平衡小樣本抽樣擾動時，表現出極高的變異度；而 Na\ïve Bayes 與 Logistic Regression 則展現了相對較高的穩定性。
