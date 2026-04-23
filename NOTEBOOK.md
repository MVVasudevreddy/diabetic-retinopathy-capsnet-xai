# Jupyter Notebook

## Google Colab Notebook

The complete implementation notebook for this project is available on Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/18jjm6KwuVkep8pGVeaK2P21yaxYubDfr)

**Direct Link**: [CapsNetXAI_Final.ipynb](https://colab.research.google.com/drive/18jjm6KwuVkep8pGVeaK2P21yaxYubDfr)

## Notebook Contents

The Colab notebook includes:
- Complete CapsNet implementation with custom layers
- Data preprocessing pipeline (CLAHE, Augmentation, Normalization)
- Model training with callbacks (EarlyStopping, ReduceLROnPlateau, ModelCheckpoint)
- Grad-CAM explainability implementation
- Performance evaluation (Accuracy, Precision, Recall, F1-Score, Confusion Matrix)
- Result visualizations (Training curves, Grad-CAM heatmaps, ROC curves)

## Running the Notebook

1. Click the "Open in Colab" badge above
2. Make a copy to your Google Drive (File → Save a copy in Drive)
3. Enable GPU: Runtime → Change runtime type → Hardware accelerator → GPU
4. Run all cells sequentially

## Requirements

The notebook automatically installs all required dependencies:
```
tensorflow>=2.8.0
albumentations>=1.2.0
opencv-python
scikit-learn
matplotlib
tqdm
```

## Dataset

The notebook uses the APTOS 2019 Blindness Detection dataset from Kaggle. You'll need to:
1. Download from: https://www.kaggle.com/competitions/aptos2019-blindness-detection
2. Upload to your Google Drive
3. Mount Drive in the notebook (first cell)

---

*For questions or issues with the notebook, please open an issue in this repository.*
