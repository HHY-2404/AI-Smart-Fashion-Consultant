# AI-Smart-Fashion-Consultant
👗 AI Smart Fashion Consultant (AI 智慧穿搭顧問系統)

📖 專案簡介 (Project Overview)

本專案旨在提供「智慧零售（Smart Retail）」的數據解決方案。
在現今電商環境中，服飾退貨率居高不下，主因在於消費者難以掌握自身真實體型與適合的色系。本系統結合電腦視覺 (Computer Vision) 與 機器學習 (Machine Learning) 技術，透過單張照片即可自動進行特徵萃取，精準判斷使用者的「身形比例」與「臉部膚色」，並輸出客製化的穿搭建議，進而協助服飾電商降低退貨率、提升轉換率。

✨ 核心技術與功能 (Core Features)

1. 影像資料清理與前處理 (Data Cleaning & Preprocessing)

導入 OpenCV 進行影像讀取與色彩空間轉換 (BGR to RGB)。

實作防呆機制：自動過濾無法偵測到人臉或完整身形的無效影像，確保後續演算法的穩定度。

2. 身形關鍵點偵測 (Body Pose Estimation)

採用 MediaPipe Pose 深度學習模型，精準定位肩膀、腰部、骨盆等核心人體關鍵點。

演算法邏輯：透過幾何距離計算肩寬與骨盆寬度比例，利用 Rule-based 邏輯將使用者分類為「蘋果型」、「梨型」、「倒三角型」等，並給予對應的修飾穿搭建議。

3. 膚色特徵資料挖掘 (Skin Tone Data Mining)

利用身形關鍵點框出「臉部感興趣區域 (ROI)」。

運用 K-Means 分群演算法 (K-Means Clustering) 進行像素級別的資料挖掘，排除背景與陰影雜訊，精準萃取出使用者臉部的主要 RGB 色碼。

依據色彩學邏輯判斷冷暖色調，推薦最適合的服飾顏色。

📂 專案架構 (Project Structure)

(註：這是模組化後的理想架構)

AI_Fashion_Consultant/
│
├── data/                  # 測試用影像資料夾
├── notebooks/             # 實驗與演算法開發 (Jupyter Notebook)
│   └── s1122026.ipynb     # 核心演算法原型
│
├── src/                   # 模組化原始碼
│   ├── pose_detector.py   # 身形偵測模組
│   ├── color_miner.py     # KMeans 膚色萃取模組
│   └── recommender.py     # 穿搭建議邏輯模組
│
├── README.md              # 專案說明書
└── requirements.txt       # 環境依賴套件清單


🚀 未來展望 (Future Work)

[進行中] 導入大語言模型 (LLM)：預計串接 OpenAI/Gemini API，將生硬的條件判斷式升級為 NLP 自然語言生成，打造具備專業服裝設計師口吻的 AI 顧問。

[規劃中] 模型升級：收集真實服飾資料集，訓練卷積神經網路 (CNN) 進行單品圖像辨識。
