# Intelligent Waste Classification Using CNN and Transfer Learning

## Project Overview

This project builds an **Intelligent Waste Classification System** using Deep Learning and Computer Vision. It automatically classifies waste images into two categories:

- **O** — Organic Waste
- **R** — Recyclable Waste

### Models Used
- Baseline CNN
- Transfer Learning with VGG19
- Enhanced Deep CNN

> **Environment:** This project is designed to run entirely on **Google Colab**.

---

## Problem Statement

Manual waste sorting is time-consuming, error-prone, expensive, and inconsistent. Improper segregation reduces recycling efficiency and increases environmental pollution. This project uses image classification models to automate waste category identification.

---

## Project Objectives

- Build a baseline CNN model for waste classification
- Apply transfer learning using VGG19
- Develop an enhanced deep CNN architecture
- Compare model performances
- Analyze overfitting and generalization
- Improve automated waste segregation accuracy

---

## Dataset

**Source:** [Waste Classification Data — Kaggle](https://www.kaggle.com/datasets/techsash/waste-classification-data/data)

### Structure

```
DATASET/
├── TRAIN/
│   ├── O/
│   └── R/
└── TEST/
    ├── O/
    └── R/
```

### Size

| Split      | Images |
|------------|--------|
| Training   | 18,052 |
| Validation |  4,512 |
| Testing    |  2,513 |
| **Total**  | **25,077** |

---

## Technologies Used

- **Language:** Python
- **Framework:** TensorFlow / Keras
- **Libraries:** NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn

---

## How to Run on Google Colab

### Step 1: Open a New Colab Notebook

Go to [https://colab.research.google.com](https://colab.research.google.com) and create a new notebook.

---

### Step 2: Install the Kaggle API

```python
!pip install kaggle
```

---

### Step 3: Upload Your Kaggle API Key

Download `kaggle.json` from your Kaggle account → **Account → API → Create New Token**, then upload it in Colab:

```python
from google.colab import files
files.upload()  # Upload kaggle.json
```

Then move it to the correct location:

```python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

---

### Step 4: Download the Dataset

```python
!kaggle datasets download -d techsash/waste-classification-data
!unzip waste-classification-data.zip -d DATASET
```

---

### Step 5: Install Required Libraries

Most libraries are pre-installed in Colab. If anything is missing:

```python
!pip install tensorflow numpy pandas matplotlib seaborn scikit-learn
```

---

### Step 6: Set Dataset Paths

```python
train_dir = "/content/DATASET/TRAIN"
test_dir  = "/content/DATASET/TEST"
```

---

### Step 7: Run the Notebook

Execute all cells in order (Runtime → Run All), or run them one by one.

---

### Optional: Mount Google Drive

To save models or outputs permanently:

```python
from google.colab import drive
drive.mount('/content/drive')

# Save model example
model.save('/content/drive/MyDrive/waste_classification_model.h5')
```

---

## Data Preprocessing

| Step | Details |
|------|---------|
| Image Size | 224 × 224 px |
| Normalization | Pixel values rescaled to [0, 1] |
| Augmentation | Rotation, Zoom, Horizontal Flip |

---

## Training Configuration

| Parameter | Value |
|-----------|-------|
| Image Size | 224 × 224 |
| Batch Size | 32 |
| Optimizer | Adam |
| Loss Function | Categorical Crossentropy |
| Epochs | 10–15 |
| Early Stopping | Enabled |

---

## Models

### 1. Baseline CNN
Conv2D → MaxPooling (×3) → Flatten → Dense → Softmax

Acts as the benchmark model.

### 2. VGG19 (Transfer Learning)
Pretrained on ImageNet. Custom head added: Flatten → Dense → Dropout → Softmax

### 3. Enhanced Deep CNN
Adds Batch Normalization, extra Conv layers, and Dropout to reduce overfitting.

---

## Results

| Model | Accuracy | Notes |
|-------|----------|-------|
| Baseline CNN | 89% | Good, but overfitting observed |
| **VGG19** | **89%** | **Best — stable, generalizes well** |
| Enhanced CNN | 84% | Training instability observed |

### Best Model: VGG19
- Stable validation accuracy
- Better feature extraction
- Lower overfitting
- Best generalization

---

## Outputs Generated

- Training & validation accuracy/loss graphs
- Confusion matrices
- Classification reports (Precision, Recall, F1-score)
- Final model performance metrics

---

## Challenges

- Visual similarity between waste categories
- Class imbalance
- Background noise and lighting variations
- Overfitting in the baseline CNN

---

## Future Improvements

- **Multi-class classification** — Plastic, Glass, Metal, Paper, Cardboard
- **Better architectures** — ResNet, EfficientNet, MobileNet
- **Handle class imbalance** — Focal Loss, Oversampling, Class Weights
- **Hyperparameter tuning** — Learning rate, Batch size, Dropout rate

---

## Conclusion

This project demonstrates how Deep Learning and Transfer Learning can power intelligent waste classification. The VGG19 model achieved the best results with high accuracy, stable validation performance, and strong generalization — making it suitable for smart recycling systems, smart bins, and automated waste management in smart city applications.

---

*This project is for educational and research purposes.*
