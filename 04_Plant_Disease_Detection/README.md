# Plant Disease Detection Using CNN

## Overview
This project uses a Convolutional Neural Network (CNN) to classify plant leaf images into plant-disease categories. It is intended as an educational computer-vision project and a starting point for exploring image classification.

## Objectives
- Load and prepare plant-leaf images for multi-class classification.
- Resize images to a consistent input shape and normalize pixel values.
- Train a CNN to predict one of 38 classes.
- Evaluate predictions on a held-out validation set.
- Try the trained model on an example leaf image.

## Dataset
- **Dataset:** PlantVillage Tiny (`geraldmc/plantvillage-tiny`, hosted on Hugging Face)
- **Images:** 1,900
- **Classes:** 38
- **Input size:** 128 × 128 RGB
- **Split:** 80% training (1,520 images), 20% validation (380 images), stratified by class

The notebook uses this smaller dataset because the attempted TFDS download source was unavailable in the runtime.

## Model and workflow
1. Load the image dataset and class labels.
2. Resize images to 128 × 128 and normalize pixel values to the range 0–1.
3. Train a CNN with convolution, max-pooling, dense, and dropout layers.
4. Use early stopping and learning-rate reduction callbacks.
5. Evaluate the restored model on the validation set and inspect example predictions.

The CNN contains three convolutional blocks (32, 64, and 128 filters), followed by a dense layer with 128 units, dropout, and a 38-unit softmax output.

## Results
- The best checkpoint was restored using validation loss.
- **Validation accuracy:** approximately 52.9% for the restored checkpoint.
- **Macro F1-score:** approximately 0.51.
- **Weighted F1-score:** approximately 0.51.

Results vary by class. Some classes perform better than others, and the gap between training and validation performance suggests overfitting. These results are a baseline, not a reliable plant-diagnosis system. An example image prediction with high confidence does not guarantee accuracy on new images.

## Repository contents
Expected folder structure:

```text
04_Plant_Disease_Detection/
├── Plant_Disease_Detection.ipynb
├── README.md
└── requirements.txt
```

## Run in Google Colab
1. Open `Plant_Disease_Detection.ipynb` in Google Colab.
2. Run the notebook cells in order.
3. Allow the dataset and required packages to load.
4. Review the training curves, classification report, confusion matrix, and example predictions.

## Run locally
Use Python 3.10 or a compatible Python version supported by your installed TensorFlow release.

```bash
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter:

```bash
jupyter notebook
```

Open `Plant_Disease_Detection.ipynb` and run the cells. Dataset-loading code may require an internet connection.

## Limitations
- The dataset is small compared with the full PlantVillage collection.
- Validation performance is moderate and indicates that generalization needs improvement.
- Images taken in real fields may differ from the dataset in lighting, background, camera quality, and leaf condition.
- The model should not be used as the sole basis for agricultural or plant-health decisions.

## Future improvements
- Train with a larger, more diverse dataset.
- Apply data augmentation and transfer learning (for example, MobileNetV2).
- Tune hyperparameters and evaluate per-class errors.
- Test on independently collected field images.
- Save model artifacts separately if they are too large for the GitHub repository.

## License and attribution
Credit the PlantVillage Tiny dataset source (`geraldmc/plantvillage-tiny`) and review its dataset card and license before redistributing data or derived artifacts.
