# Cat vs. Dog Image Classification Project

## 1. Project Overview

This project documents the end-to-end process of building, training, and evaluating a Convolutional Neural Network (CNN) to classify images of cats and dogs. The project starts with a custom CNN model trained from scratch and includes extensive testing on multiple datasets to evaluate its real-world performance.

The primary goal is to establish a strong baseline model and then use its performance metrics to justify and guide future improvements, such as implementing Transfer Learning.

---

## 2. Key Features

- **CNN from Scratch:** A custom CNN model built with TensorFlow/Keras.
- **Robust Data Pipeline:** Handles large, messy datasets by cleaning and filtering invalid images on the fly.
- **Checkpointing:** Implements a dual-save strategy to save both the best-performing model and the last completed epoch.
- **Comprehensive Evaluation:** The model is evaluated against three different data sources:
  1. A validation set from the original training data.
  2. A large, unseen dataset from Kaggle.
  3. Live, random images fetched from the Unsplash API.
- **Detailed Reporting:** Generates and saves detailed performance reports, including accuracy, precision, recall, and a confusion matrix.

---

## 3. Project Structure

The repository is organized to separate the different phases of the project for clarity and modularity.

```plaintext
cat-dog-classification/
│
├── notebooks/
│   ├── 1_Model_Training_and_Evaluation.ipynb
│   └── 2_Advanced_Inference_Tests.ipynb
│
├── saved_models/
│   └── README.md  (Contains the download link for the model)
│
├── reports/
│   ├── manual_test_report.txt
│   └── test_reports/
│       ├── large_dataset_report_... .txt
│       └── unsplash_report_... .txt
│
├── test_images/
│   ├── cats/
│   └── dogs/
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 4. Setup and Installation

To run this project, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cat-dog-classification.git
   cd cat-dog-classification
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download the Trained Model:**  
   The model file (`best_model.keras`) is too large for GitHub and is hosted on Google Drive.  
   Please follow the instructions in the `saved_models/README.md` file to download it and place it in the correct directory.

5. **API Credentials:**  
   Before running the notebooks, you must create `kaggle.json` and `Unsplash.json` files with your API keys.  
   The notebooks will prompt you to upload these files when run in a new session.

---

## 5. Usage

The project is divided into two main notebooks, designed to be run in order:

1. **`notebooks/1_Model_Training_and_Evaluation.ipynb`:**  
   Run this notebook first. It handles the entire training process and saves the final `best_model.keras` checkpoint to your Google Drive (this file is not tracked by Git). This trained model is required by the second notebook.

2. **`notebooks/2_Advanced_Inference_Tests.ipynb`:**  
   After the model has been trained and saved by the first notebook, run this one. It loads the `best_model.keras` from your Google Drive and performs advanced tests on new data sources.

---

## 6. Results Summary

The custom CNN model achieved a strong baseline performance:

- **Validation Accuracy:** Reached a peak of ~87–88% on the validation set from the original dataset.
- **Real-World Generalization:** When tested on a different, large Kaggle dataset, it maintained this accuracy.
- **Live API Test (Unsplash):** Accuracy dropped to ~72%, highlighting the performance gap between curated datasets and random, "in-the-wild" images. This result successfully establishes the need for more advanced techniques.

---

## 7. Next Steps

The next phase of this project is to implement **Transfer Learning** using a pre-trained model (e.g., MobileNetV2) to bridge the performance gap and achieve an accuracy of **>95%**.
