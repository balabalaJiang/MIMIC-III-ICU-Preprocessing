# 學習歷程 - 提示詞紀錄(PROMPT LOG)
學號： 1258001
姓名： 江永閎

以下紀錄在完成本次MIMIC-III前處理作業時，與AI(Gemini)的主要互動提示詞與輔助過程：

## 紀錄一：任務拆解與Notebook架構規劃
* 我的提示詞(Prompt)：
  1. `(列出作業規範與要求)`根據上述內容，一步一步說明操作步驟。
  2. 詳細說明階段二(Jupyter Notebook)的內容、做法與程式碼流程等。

* AI的協助：
  * 將繁雜的作業說明拆解成五個明確的執行階段。
  * 提供了一份完整的Jupyter Notebook實作指南(包含資料讀取、EDA視覺化、缺失值處理、特徵工程與存檔的Python程式碼骨架)，確保流程符合「可重現性」的要求。

* 我的後續操作：
  * 依照AI提供的架構，在自己的Jupyter environment中建立Code與Markdown區塊，並逐步執行驗證。

## 紀錄二：異常排解並撰寫數據分析文字報告(Markdown)
* 我的提示詞(Prompt)：
  1. ModuleNotFoundError: No module named 'seaborn'
  2. FileNotFoundError: [Errno 2] No such file or directory
  3. 以下為訓練成果數據，根據這些數據修改Markdown等部分:
      * 缺失率大於40%的欄位:[] (附上長條圖)
      * 連續變數分佈與異常值觀察(附上年齡、住院天數等分佈圖)
      * 類別變數與目標變數關係(附上入院類型等圖表)
      * 重點統計表與具體觀察:(附上groupby算出的各類別實際人數、平均住院天數與死亡率表格)
  4. 說明markdown語法

* AI的協助：
  * 依照我實際遇到的具體Bug(Seaborn未安裝)給予解決方法。
  * 依照我實際遇到的具體Bug(字串格式化f-string遺漏)給予解決方法。
  * 根據我實際跑出的數據與圖表(例如：急診人數高達42,071人且死亡率12.92%、新生兒族群分佈、缺失率皆低於40%等)，將這些客觀數字帶入`A1_<學號>.md`的文字報告模板中。
  * 確保報告格式完全符合助教規定的6大標題，並將EDA的具體觀察有條理地列出。
  * 補充說明了Markdown的語法與排版規則。

* 我的後續操作：
  * 根據AI建議，重新修改程式碼並執行。
  * 檢查AI生成的報告內容是否與我的圖表完全一致，並補充部分個人反思與未來建模的延伸方向。
  * 運用Markdown語法檢視並調整報告的標題與表格呈現。

## 紀錄三：紀錄撰寫
* 我的提示詞(Prompt)：
  1. Jupyter Notebook實作指南(階段二)的.csv檔案太大無法開啟
  2. 協助撰寫README.md、requirements.txt、DEBUG_LOG.md、PROMPT_LOG.md

* AI的協助：
  * 解釋One-Hot Encoding後特徵矩陣變大是正常現象，並建議直接使用Pandas的`pd.read_csv()`進行檢查，而非使用Excel硬開，化解了對檔案損壞的疑慮。
  * 說明`README.md`、`requirements.txt`、`DEBUG_LOG.md`、`PROMPT_LOG.md`所需的內容、格式以及注意事項，並協助撰寫大綱。

* 我的後續操作：
  * 使用Pandas確認`df_model_ready.csv`讀取正常。
  * 根據AI生成的大綱撰寫並修改`README.md`、`requirements.txt`、`DEBUG_LOG.md`、`PROMPT_LOG.md`之內容。
  * 將生成的Log記錄歸檔，準備進行最終的專案打包。
