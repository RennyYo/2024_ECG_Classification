# 🩺 ECG 影像數據集分類專案 (ECG Image Classification Project)

---

## 🚀 專案目標與方法 (Goal and Methodology)

### 🎯 專案目標
使用國立成功大學醫學院附設醫院 (NCKU Hospital) 提供的 ECG 影像數據集，進行**心電圖 (ECG) 影像分類**。

### 📋 數據處理 (Data Pre-processing)
* 轉換為**灰階 (Grayscale)**。
* 統一**調整影像尺寸 (Resize)**。
* 進行數據**正規化 (Regularization)**。

### 📊 數據集劃分 (Dataset Splitting)
將數據集劃分為**訓練集 (Training)**、**測試集 (Testing)** 和**驗證集 (Validation)**。

---

## 🛠️ 模型與優化 (Model and Optimization)

### 🧠 核心模型
* 使用**遷移學習 (Transfer Learning)** 策略。
* 基礎模型採用 **ResNet50**。

### ⚙️ 參數調校與比較 (Parameter Tuning)

| 類別 | 參數名稱 | 實驗值 |
| :--- | :--- | :--- |
| **優化器 (Optimizer)** | 比較 | `Adam` / `RMSprop` / `SGD` |
| **學習率 (Learning Rate)** | 比較 | `0.1` / `0.01` / `0.001` / `0.0001` |

### 🧩 外部卷積層 (External CNN Layer)
* **附掛**一個額外的卷積神經網絡 (CNN) 層。
* 修改其內部參數：`filter`、`padding`、`stride`、`pooling`。

---

## 📈 實驗結果 (Experimental Results)

| 設定條件 | 訓練週期 (Epoch) | 額外 CNN 層 | 準確率 (Accuracy) |
| :--- | :--- | :--- | :--- |
| **RMSprop**, LR = `0.001` | `30` | 否 | **0.6881** |
| **RMSprop**, LR = `0.0015` | `15` | 是 (`+CNN`) | **0.9996** |

**結論：** 在基礎 ResNet50 上**附掛額外的 CNN 層**，並微調學習率至 `0.0015`，能大幅提高模型的分類準確率。
