# Machine Learning Fundamentals — Coursework & Final Project

Academic **Machine Learning Fundamentals** coursework completed during the **2025/2026 Erasmus+ exchange at Brno University of Technology**.

This repository brings together Jupyter notebooks from the course and a collaborative final deep-learning project. The original coursework notebooks are kept with their course filenames.

## Repository contents

- **[Final project — Room Occupancy Classification Using Deep Learning](./MPA_MLF_Final_Project_Rafael_Miguel_%281%29%20%281%29.ipynb):** four-class occupancy prediction using radar images and EfficientNet-B0. Developed jointly by Rafael Estévez Marrero and Miguel Martín de las Heras.
- **Coursework notebooks:** the other exercise and lab notebooks in this repository cover assignments from the Machine Learning Fundamentals course.

## Featured final project: Room Occupancy Classification Using Deep Learning

**Classifying the number of people in a room from 60 GHz radar images using EfficientNet-B0.**

Academic final project for **Machine Learning Fundamentals** at **Brno University of Technology** (2025/2026 Erasmus+).

**Authors:** Rafael Estévez Marrero and Miguel Martín de las Heras

## Project overview

The goal was to predict room occupancy from **60 GHz delay-Doppler radar snapshots**, distinguishing four classes:

| Class | Meaning |
| --- | --- |
| 0 | Empty room (or machine only) |
| 1 | One person |
| 2 | Two people |
| 3 | Three people |

Although stored as images, delay-Doppler snapshots represent radar measurements rather than conventional photographs. The challenge was to learn patterns that distinguish occupancy levels while handling an imbalanced dataset.

## Dataset

| Split | Images | Labels |
| --- | ---: | --- |
| Training data | 9,227 | Available |
| Test data | 3,955 | Not provided |

The labeled training data was further divided into **stratified training and validation subsets (80/20)**. The test set was used to generate predictions for submission; the metrics below are **validation results**, not test-set scores.

The dataset is **not included in this repository**.

## Method

1. **Preprocessing:** resized images to 64 × 64 pixels, converted them to RGB and normalized the inputs.
2. **Data augmentation:** applied transformations to improve generalization.
3. **Model:** adapted an ImageNet-pretrained **EfficientNet-B0** using transfer learning and a custom four-class classification head.
4. **Class imbalance:** used class-weighted cross-entropy loss to reduce bias toward more frequent occupancy classes.
5. **Training:** used **AdamW**, cosine learning-rate scheduling and model checkpointing based on validation accuracy.
6. **Evaluation:** assessed accuracy, macro F1-score, per-class performance and a confusion matrix; generated a CSV of test predictions.

## Results

| Metric | Validation result |
| --- | ---: |
| **Accuracy** | **95.77%** |
| **Macro F1-score** | **0.9508** |

The reported validation results are taken from the project's final academic report. These figures **must not be interpreted as performance on the unlabeled test set**.

## Technologies

**Python · PyTorch · torchvision · EfficientNet-B0 · scikit-learn · NumPy · Pandas · Matplotlib**

## Explore the project

**[Open the final project notebook](./MPA_MLF_Final_Project_Rafael_Miguel_%281%29%20%281%29.ipynb)**

The repository also contains coursework from the Machine Learning Fundamentals course. The linked Jupyter notebook contains the final project's data pipeline, model implementation, training and evaluation workflow.

### Running the notebook

The notebook was developed for **Google Colab** and mounts Google Drive. To run it:

1. Open the notebook in Google Colab.
2. Make the dataset available in your own Google Drive.
3. Update the notebook's `BASE_DIR` and related dataset paths to your directory structure.
4. Install any missing Python dependencies, then run the cells in order.

The input dataset and trained model weights are not distributed with the repository, so reproducing the exact reported results requires access to the original data and training setup.

## Academic context and credits

Developed **jointly by Rafael Estévez Marrero and Miguel Martín de las Heras** during their Erasmus+ studies at **Brno University of Technology**, as part of *Machine Learning Fundamentals*. Both authors are credited for the collaborative project.

---

*This repository documents an academic machine-learning project; it is not a deployed real-time occupancy-monitoring system.*
