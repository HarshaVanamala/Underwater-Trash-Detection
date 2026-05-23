# 🌊 Underwater Trash Detection using YOLOv8s

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![YOLOv8](https://img.shields.io/badge/YOLOv8s-Ultralytics-purple?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red?style=flat-square&logo=pytorch)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

A deep learning system for detecting underwater trash and marine debris using YOLOv8s, trained on the TrashCan dataset. Built to support marine pollution monitoring and future AUV deployment.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Results](#results)
- [Project Structure](#project-structure)
- [Dataset](#dataset)
- [Model Weights](#model-weights)
- [Installation](#installation)
- [Usage](#usage)
- [Training Configuration](#training-configuration)
- [Future Scope](#future-scope)
- [License](#license)

---

## 🎯 Overview

This project builds a real-time underwater object detection pipeline capable of:

- Detecting marine debris and plastic waste in underwater images
- Differentiating trash from natural underwater objects
- Supporting future deployment on Autonomous Underwater Vehicles (AUVs)
- Enabling scalable marine pollution monitoring

**Model:** YOLOv8s (Small) | **Framework:** PyTorch + Ultralytics | **Input Resolution:** 640×640  
**Training Hardware:** NVIDIA Tesla T4 GPU (Google Colab)

---

## 📊 Results

| Metric | Score |
|---|---|
| Precision | 0.848 |
| Recall | 0.735 |
| mAP@0.5 | 0.802 |
| mAP@0.5:0.95 | 0.551 |

Sample predictions are available in the `final_predictions/` folder. Evaluation plots (confusion matrix, PR curves) are in `evaluation_results/`.

---

## 📂 Project Structure

```
underwater-trash-detection/
│
├── 📁 notebooks/
│   ├── 01_preprocessing.ipynb       # Dataset cleaning and augmentation
│   ├── 02_training.ipynb            # YOLOv8s model training
│   ├── 03_evaluation.ipynb          # Metrics and evaluation plots
│   └── 04_inference.ipynb           # Run predictions on new images
│
├── 📁 models/
│   └── trashcan_base_best.pt        # Trained model weights (download separately)
│
├── 📁 evaluation_results/           # mAP curves, confusion matrix, loss plots
├── 📁 final_predictions/            # Sample output images with bounding boxes
├── 📁 test_images_real/             # Real-world test images
│
├── trashcan.yaml                    # Dataset configuration file
├── requirements.txt                 # Python dependencies
├── .gitignore
└── README.md
```

---

## 🗃️ Dataset

The project uses the [TrashCan Dataset](https://conservancy.umn.edu/handle/11299/214865) — a public dataset of annotated underwater waste images captured in real marine environments.

**Dataset characteristics:**
- Real underwater environments with diverse lighting
- Plastic waste, debris, and natural underwater objects
- Bounding box annotations in YOLO format

> ⚠️ The `processed_dataset/` folder is **not included in this repository** due to file size constraints.
**Local path (development machine):**
```
C:\Users\harsha\Desktop\Underwater-Trash-Detection\processed_dataset
```

**To reproduce the processed dataset:**
1. Download the raw dataset from the [TrashCan Dataset page](https://conservancy.umn.edu/handle/11299/214865)
2. Place the contents in a `raw_data/` folder at the project root
3. Run `notebooks/01_preprocessing.ipynb` to generate the processed version

### ⚙️ Preprocessing & Augmentation

Techniques applied during preprocessing:

- Image resizing to 640×640
- Auto-orientation and label verification
- Horizontal flipping
- Rotation augmentation
- Brightness adjustment
- Blur augmentation

---

## 🧠 Model Weights

The trained model weights (`trashcan_base_best.pt`) are hosted on Google Drive due to GitHub's file size limits.

| File | Description | Size | Link |
|------|-------------|------|------|
| `trashcan_base_best.pt` | Best checkpoint from 100-epoch training | ~22MB | [Download from Google Drive](https://drive.google.com/file/d/16vGWVdfm5f55NtQvWVsN-bfmvXwqgcXP/view?usp=sharing) |

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/HarshaVanamala/underwater-trash-detection.git
cd underwater-trash-detection
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download model weights

Download `trashcan_base_best.pt` from the [Google Drive link](#model-weights) above and place it in the `models/` folder.

---

## 🚀 Usage

### Run inference on a single image

```python
from ultralytics import YOLO

model = YOLO("models/trashcan_base_best.pt")
results = model.predict("test_images_real/your_image.jpg", conf=0.25)
results[0].show()
```

### Run inference on a folder

```python
results = model.predict("test_images_real/", conf=0.25, save=True)
```

### Run the full pipeline via notebooks

| Notebook | Purpose |
|---|---|
| `01_preprocessing.ipynb` | Clean and prepare the dataset |
| `02_training.ipynb` | Train YOLOv8s from scratch |
| `03_evaluation.ipynb` | Generate metrics and evaluation plots |
| `04_inference.ipynb` | Run predictions on new images |

---

## 🏋️ Training Configuration

| Parameter | Value |
|-----------|-------|
| Model | YOLOv8s |
| Epochs | 100 |
| Batch Size | 8 |
| Input Size | 640×640 |
| Optimizer | AdamW |
| Hardware | NVIDIA Tesla T4 (Google Colab) |

To retrain the model:

```python
from ultralytics import YOLO

model = YOLO("yolov8s.pt")
model.train(
    data="trashcan.yaml",
    epochs=100,
    batch=8,
    imgsz=640,
    optimizer="AdamW",
    project="runs/train",
    name="trashcan_v1"
)
```

---

## 🔮 Future Scope

- [ ] Video stream inference for real-time monitoring
- [ ] Edge AI deployment (Jetson Nano / Raspberry Pi)
- [ ] Multi-class underwater waste classification
- [ ] Improved detection in low-light underwater environments
- [ ] Integration with marine robotics and AUV systems
- [ ] Web dashboard for pollution monitoring

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

The TrashCan dataset is publicly available via the [University of Minnesota Digital Conservancy](https://conservancy.umn.edu/handle/11299/214865).

---

## 🙏 Acknowledgements

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) for the detection framework
- [TrashCan Dataset](https://conservancy.umn.edu/handle/11299/214865) for the annotated underwater waste data
- Google Colab for GPU training resources
