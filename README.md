# 🌾 Rice Leaf Disease Detection (PRCP-1001)

A Deep Learning and Computer Vision project designed to automatically detect and classify major rice leaf diseases—**Bacterial Leaf Blight**, **Brown Spot**, and **Leaf Smut**—from leaf images to support early agricultural intervention.

---

## 📌 Project Overview

Rice crops are frequently affected by foliar diseases that reduce yield and grain quality. This project performs end-to-end Exploratory Data Analysis (EDA), image preprocessing, data augmentation, and deep learning model experimentation using **Custom CNN** and **Transfer Learning (MobileNetV2)** within a single reproducible Jupyter Notebook.

### 📂 Dataset Information
* **Download Dataset:** https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1001-RiceLeaf.zip
* **Total Valid Images:** 119 RGB images (standardized to `224 × 224` pixels)
* **Disease Classes:**
  1. **Bacterial Leaf Blight** (40 images)
  2. **Brown Spot** (40 images)
  3. **Leaf Smut** (39 images)

---

## 🛠️ Technologies & Libraries Used
* **Programming Language:** Python 3
* **Data Manipulation & Analysis:** NumPy, Pandas
* **Data Visualization:** Matplotlib, Seaborn
* **Image Processing:** OpenCV, Pillow (PIL)
* **Deep Learning:** TensorFlow, Keras
* **Evaluation & Metrics:** Scikit-learn

---

## 📊 Experimental Results & Model Comparison

Four model configurations were evaluated on the test set (24 unseen images) to measure the impact of data augmentation and transfer learning fine-tuning:

| Model Configuration | Data Augmentation | Fine-Tuning | Test Accuracy | Test Loss |
| :--- | :---: | :---: | :---: | :---: |
| **Custom CNN (Baseline)** | No | N/A | 62.50% | 0.7284 |
| **Custom CNN (Augmented)** | Yes | N/A | 83.33% | 0.6505 |
| **MobileNetV2 (Frozen Base)** | Yes | No | 70.83% | 0.6977 |
| **MobileNetV2 (Fine-Tuned)** | **Yes** | **Yes (Top 30 layers)** | **87.50%** | **0.2158** |

### 🏆 Production Model Selection
The **Fine-Tuned MobileNetV2** (`rice_leaf_mobilenet_model.keras`) was selected as the final production model due to:
* **Highest Test Accuracy (87.50%)** and **Lowest Test Loss (0.2158)**.
* **+20.83% accuracy gain** from data augmentation on limited agricultural data.
* **Lightweight architecture** suitable for real-time mobile and web deployment.

---

## 🧩 Challenges Faced & Solutions Implemented

| Challenge Faced | Solution / Technique Used | Impact |
| :--- | :--- | :--- |
| **Small Dataset Size (119 Images)** | Data Augmentation (Flips, Rotations, Zoom) & Transfer Learning | Prevented overfitting and boosted Custom CNN accuracy by **+20.83%**. |
| **Varying Image Resolutions** | Standardized Resizing (`224 × 224`) & Pixel Normalization (`0–1`) | Ensured consistent input tensor dimensions across all models. |
| **Domain Gap in Pretrained Weights** | Two-Stage Fine-Tuning (Unfreezing top 30 layers at `lr=1e-5`) | Adapted ImageNet features to rice leaf lesions, reaching **87.50% accuracy**. |

---

## 🚀 How to Run the Project

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   cd PRCP-1001-Rice-Leaf-Disease-Detection
   ```

2. **Install required dependencies:**
   ```bash
   pip install numpy pandas matplotlib seaborn opencv-python pillow tensorflow scikit-learn
   ```

3. **Download the Dataset & Run:**
   * Download and extract the dataset from the link above.
   * Open `RiceLeaf disease detection.ipynb` in Jupyter Notebook or VS Code and run all cells sequentially.

---

## 🔮 Future Enhancements
* Expand the dataset with diverse field backgrounds and lighting conditions.
* Add more disease categories (*Rice Blast*, *Sheath Blight*, and *Healthy Leaves*).
* Deploy the model via **Streamlit** or **TensorFlow Lite** for mobile field diagnosis.
* Integrate **Grad-CAM** visual explanations to highlight infected leaf regions.
