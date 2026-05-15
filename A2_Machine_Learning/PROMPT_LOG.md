# AI 協作提示詞紀錄 (PROMPT LOG)
**學號：** `1258001`  |  **姓名：** `江永閎`

| 紀錄編號 | 任務階段 | 我的提示詞 (Prompt) | AI 的協助內容 | 我的後續操作 |
|:---:|---|---|---|---|
| **01** | Step 2: 資料讀取與抽樣子集 | 請協助實作 `load_mimic3c()` 與 `make_imbalanced_subset()`，並使用方案 A，同時更新四個紀錄檔。 | AI 提供了包含排除洩漏欄位 (LOSdays 等) 的載入函式，以及強制控制 10% 比例並使用 shuffle 打散順序的抽樣函式。 | 將程式碼貼入 Jupyter Notebook 測試，成功印出正確的 X.shape 與 10% 的抽樣比例，並依照 AI 指示更新了報告的洩漏清單。 |
| **02** | Step 2: Debug 抽樣錯誤 | 執行方案 A 時發現 y=1 比例為 0，且報錯原始資料不足以抽取。詢問 AI 原因。 | AI 指出這是 HW1 的目標變數被標準化破壞，且特徵維度達 17065 會有維度災難。建議並提供了切換至「方案 B」的實作程式碼。 | 採用方案 B 程式碼，成功修正標籤並瘦身矩陣，確保後續 840 次訓練能高效執行。並同步更新 README 等文件說明。 |
| **03** | Step 3: 核心模型訓練迴圈 | 詢問如何實作作業要求的 20-seed 訓練雙層迴圈。 | AI 提供了完整的 sklearn 訓練流程，並特別標示出防呆機制：(1) 模型加上 random_state=0 固定初始化。 (2) 使用 clone() 複製模型避免權重記憶。 (3) scaler 嚴格 fit_transform(train) 以防洩漏。 | 在 Jupyter Notebook 中執行這段高耗時的程式碼，成功產出包含 840 筆資料的 `mimic3c_results.csv`，完成作業的核心數據蒐集。 |
| **04** | Step 4: 統計分析與視覺化 | 請協助實作作業要求的 Paired t-test 表格、Ceiling effect 表、STD ratio 表以及 Boxplot。 | AI 提供了利用 pandas, seaborn 和 scipy 撰寫的自動化分析腳本，並特別處理了 `to_markdown()` 的表格輸出格式。 | 執行程式碼並成功在 output/ 產生所有 3 張圖片與 3 份 markdown 表格。打開圖表確認了 Random Split 在 n=100 時的巨大變異。 |
| **05** | Step 5: 撰寫報告與三大發現檢驗 | 提供 `significance_table`, `std_ratio_table` 與 `ceiling_effect_table` 的跑出數據，請 AI 協助對照 W7 報告的結論，撰寫三大發現的分析。 | AI 協助解讀了數據：指出 MIMIC3C 無天花板效應、SVM 在 n=100 的異常表現，以及深入剖析新加入的 RF 與 NB 模型對於抽樣策略敏感度的數學原因。 | 將分析內容整合進 `A2_<學號>.md`，確認數據引用正確無誤，並自行補齊研究背景與實驗反思，完成最終的專案打包與檢查。 |