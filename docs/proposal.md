# 期末研究提案：基於靜態影像的車輛違停偵測

> **研究主題**：利用靜態影像，偵測車輛是否停在紅線禁停區（違停偵測）
> - 輸入：靜態照片
> - 核心任務：Object Detection（偵測車輛 + 紅線）
> - 判斷邏輯：車輛邊界框（Bounding Box）與紅線區域是否重疊（IoU）
> - 模型架構：自建 CNN 模型（Custom CNN Architecture）

---

## 一、研究關鍵字（Keywords）

`Illegal Parking Detection`, `Object Detection`, `Custom CNN Architecture`, `Red Line Segmentation`, `Traffic Violation Recognition`, `Smart City`, `Convolutional Neural Network (CNN)`, `Intersection over Union (IoU)`

| # | 關鍵字 | 說明 |
|---|--------|------|
| 1 | `Illegal Parking Detection` | 核心任務描述 |
| 2 | `Object Detection` | 方法論類型 |
| 3 | `Custom CNN Architecture` | 自建模型架構 |
| 4 | `Red Line Segmentation` | 紅線區域識別子任務 |
| 5 | `Traffic Violation Recognition` | 上位應用領域 |
| 6 | `Smart City` | 社會應用場景 |
| 7 | `Convolutional Neural Network (CNN)` | 基礎技術架構 |
| 8 | `Intersection over Union (IoU)` | 判斷車輛與紅線重疊的核心指標 |

---

## 二、背景介紹（Background）

違規停車是都市交通管理中長期存在的問題，不僅壓縮道路空間，更可能阻礙緊急救援車輛通行。傳統人工巡邏執法受限於人力成本與排班安排，無法消弭深夜、假日等執法空窗期，導致違停行為屢禁不止。現行民眾檢舉機制雖提供另一種管道，但仍需人工審核照片、逐件判斷是否違規，處理效率低落且難以規模化。隨著卷積神經網路（Convolutional Neural Network, CNN）在影像辨識領域的快速發展，透過靜態影像自動偵測車輛是否停於紅線禁停區已具備技術可行性。本研究旨在建立一套基於自建 CNN 模型的違停偵測系統，透過識別影像中車輛邊界框與紅線區域的重疊關係（Intersection over Union, IoU），實現自動化之違停判別。此研究成果可作為智慧城市（Smart City）交通執法自動化的基礎模組，降低人力依賴並填補執法空窗。

---

## 三、研究困境（Research Challenges）

1. **視角遮蔽與幾何變形問題**
   拍攝角度不固定時，車輛本身可能遮蔽地面紅線，或透視效果導致車輛邊界框（Bounding Box）與紅線的空間關係產生形變，使模型難以準確判斷車輛是否壓線。此問題在斜角拍攝或近距離拍攝時尤為明顯。

2. **環境光線與天氣造成紅線辨識困難**
   紅線在不同光照條件下（強烈日照、陰天、夜間）及天氣影響下（積水反光、褪色路面）呈現的色彩差異顯著，模型對顏色特徵的泛化能力受訓練資料分布影響，難以在多種環境條件下維持穩定的辨識準確率。

3. **標注資料稀缺，訓練樣本不足**
   違停偵測任務需同時標注影像中的車輛邊界框與紅線區域，標注成本高且耗時。公開資料集數量有限，若需自行收集台灣本地場景影像並進行標注，將面臨資料規模不足、標注品質不一致等問題，進而影響模型訓練效果。

4. **紅色物體混淆問題**
   影像中常見的紅色物體（如交通號誌燈、車輛尾燈、紅色廣告招牌）在色彩特徵上與地面紅線相近，自建 CNN 模型若未能學習到足夠的形狀與空間上下文特徵，可能產生誤判，降低系統的精確率（Precision）。

---

## 四、資料集與收集方式（Datasets & Data Collection）

### 公開資料集（Roboflow Universe）

| # | 資料集名稱 | 影像數量 | 標注類別 | 來源連結 |
|---|-----------|---------|---------|---------|
| 1 | Illegal Parking Detection (Caraga State University) | 3,820 張 | motorcycle, vehicle | [連結](https://universe.roboflow.com/caraga-state-university-lluzz/illegal-parking-detection-8hv2g) |
| 2 | illegal parking (jiawengan) | 2,220 張 | illegal-parking | [連結](https://universe.roboflow.com/jiawengan/illegal-parking-ltiwv) |
| 3 | Illegal Parking (thesis) | 2,750 張 | illegal-parking | [連結](https://universe.roboflow.com/thesis-gsgcj/illegal-parking-qrvua) |
| 4 | illegal parking photo | 530 張 | car, red line | [連結](https://universe.roboflow.com/illegal-parking-photo/illegal-parking-photo-6fair) |
| 5 | illegal parking line2 | 134 張 | car, motobike, red_line | [連結](https://universe.roboflow.com/seung-bvyil/illegal-parking-line2-u55mj) |
| 6 | illegal parking (illegal-parking) | 143 張 | car, redline, whiteline, yellowline | [連結](https://universe.roboflow.com/illegal-parking/illegal-parking-ijtge) |

> ⚠️ 注意：上述資料集多為東南亞場景，台灣本地紅線樣式可能有所差異，需評估是否需要補充本地資料。

### 自行收集方式（待討論）

> 🔲 *待補充*

---

*最後更新：2026-04-08*
