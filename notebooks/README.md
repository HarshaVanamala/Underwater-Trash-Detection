# 📓 Notebooks

All notebooks are hosted on Google Colab. Click the links below to open them directly.

| # | Notebook | Description | Open in Colab |
|---|----------|-------------|---------------|
| 01 | `01_data_preprocessing.ipynb` | Dataset cleaning, augmentation, and YOLO format preparation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_7NdLgFY63jF8Xa7Lxrqg7DaWRa7VgWE) |
| 02 | `02_model_training.ipynb` | YOLOv8s training on TrashCan dataset for 100 epochs | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1IpFmG9RINlcj2O3zekKz2VSEq-RYEEMm) |
| 03 | `03_model_evaluation.ipynb` | Metrics, confusion matrix, PR curves, mAP evaluation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Dg7IvEqEYgMTpBRQUIEQeo6IiPnl7FqX) |
| 04 | `04_inference_demo.ipynb` | Run predictions on new underwater images | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Q4pQeWYMLJif000h6upD98iyJZgsjL-G) |

## 📌 Notes

- All notebooks were developed and trained on **Google Colab** using an NVIDIA Tesla T4 GPU
- Run notebooks in order (01 → 02 → 03 → 04) for full pipeline reproduction
- Make sure to mount your Google Drive at the start of each notebook
- Download `trashcan_base_best.pt` from the [model weights link](../README.md#-model-weights) before running notebooks 03 and 04
