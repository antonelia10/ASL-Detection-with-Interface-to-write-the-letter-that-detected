# ASL-Detection-with-Interface-to-write-the-letter-that-detected

# 🤟 ASL Letter Detection — Graduation Project

A deep learning project that detects **American Sign Language (ASL) hand signs** and converts them into English letters using a Convolutional Neural Network (CNN).

The project includes data exploration, preprocessing, CNN model training, evaluation, error analysis, and a Gradio-based interface that allows users to upload an image or use a webcam to detect ASL letters.

---

## 📌 Project Overview

American Sign Language is a visual language that uses hand shapes and movements to communicate.

The goal of this project is to build a computer vision system that can recognize ASL alphabet hand signs from images and predict the corresponding English letter.

The trained model can be used through a simple **Gradio interface**, where users can:

* 📷 Upload a hand-sign image
* 🎥 Capture a hand sign using a webcam
* 🤖 Detect the corresponding ASL letter
* 📝 Build a sequence of detected letters
* 🔄 Clear the detected text

> **Note:** The letters **J** and **Z** are not supported because their ASL signs require hand movement rather than a static hand position.

---

## 🧠 Model Architecture

The project uses a **Convolutional Neural Network (CNN)** built with TensorFlow/Keras.

The architecture contains:

1. Input layer — `28 × 28 × 1`
2. Convolutional layer — 32 filters
3. Batch Normalization
4. Max Pooling
5. Convolutional layer — 64 filters
6. Batch Normalization
7. Max Pooling
8. Convolutional layer — 128 filters
9. Batch Normalization
10. Max Pooling
11. Flatten layer
12. Dense layer — 128 neurons
13. Dropout — 0.4
14. Output layer — Softmax classification

The model is compiled using:

* **Optimizer:** Adam
* **Loss:** Sparse Categorical Crossentropy
* **Metric:** Accuracy

---

## 📊 Dataset

The dataset contains grayscale images representing ASL alphabet hand signs.

| Dataset  | Samples |    Features |
| -------- | ------: | ----------: |
| Training |  27,455 | 785 columns |
| Testing  |   7,172 | 785 columns |

Each image contains:

* `28 × 28 = 784` pixel values
* One label representing the ASL letter

The project maps numerical labels to alphabet letters.

### Supported Letters

The model recognizes static ASL alphabet signs except:

* **J**
* **Z**

These two letters require motion and therefore cannot be reliably represented by a single static image.

---

## 🔧 Data Preprocessing

The project prepares the image data before training the CNN.

The images are converted into the required format:

```text
28 × 28 × 1
```

Pixel values are normalized to the range:

```text
0 → 1
```

Data augmentation is also used during training to improve the model's ability to generalize to different hand-sign images.

---

## 🏋️ Model Training

The CNN is trained using:

```text
Epochs: 15
Batch Size: 128
Optimizer: Adam
```

The training process uses:

* Early Stopping
* Model Checkpointing
* Validation data
* Data augmentation

The best-performing model is automatically saved during training.

---

## 📈 Model Evaluation

The project evaluates the trained model using several methods.

### Test Accuracy

The model is evaluated on the separate test dataset to measure its classification performance.

### Classification Report

A classification report is generated containing:

* Precision
* Recall
* F1-score
* Support

for each detected letter.

### Confusion Matrix

A confusion matrix is generated to visualize which ASL letters are correctly classified and which letters are commonly confused with each other.

### Per-Class Accuracy

The project also calculates the accuracy of each individual letter and identifies the five worst-performing classes.

### Misclassified Images

The project displays examples of incorrectly classified images, showing:

```text
True: A | Pred: B
```

This helps analyze common model errors.

---

## 🖥️ Gradio Interface

The project includes a simple interactive interface built using **Gradio**.

Users can provide an image through:

* 📁 Image upload
* 📷 Webcam

After clicking **Detect Letter**, the model predicts the ASL letter and displays its confidence.

For example:

```text
Detected: A (confidence: 98.5%)
```

The detected letters are accumulated in a text box, allowing multiple predictions to be combined into a sequence.

---

## 📂 Project Structure

```text
ASL-Letter-Detection/
│
├── Grade_Project.ipynb
│
├── model_outputs/
│   ├── best_model.keras
│   └── final_model.keras
│
├── README.md
│
└── requirements.txt
```

---

## 🛠️ Technologies Used

* **Python**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **TensorFlow / Keras**
* **Gradio**
* **PIL**

---

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

Move into the project directory:

```bash
cd YOUR-REPOSITORY
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it.

### macOS / Linux

```bash
source .venv/bin/activate
```

### Windows

```bash
.venv\Scripts\activate
```

Install the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow gradio pillow
```

---

## ▶️ How to Run

Open the notebook:

```bash
jupyter notebook Grade_Project.ipynb
```

Run the notebook cells in order.

After training the model, the Gradio interface can be launched from the notebook.

The application will provide an interface where you can upload an ASL hand-sign image or use your webcam.

---

## 💾 Saved Models

The trained models are saved inside:

```text
model_outputs/
```

### Best Model

```text
model_outputs/best_model.keras
```

### Final Model

```text
model_outputs/final_model.keras
```

The final model can be loaded using TensorFlow/Keras:

```python
from tensorflow import keras

model = keras.models.load_model(
    "model_outputs/final_model.keras"
)
```

---

## 🎯 Project Goals

The main goals of this project are to:

* Build an image classification model for ASL signs
* Apply image preprocessing and augmentation
* Train a CNN for hand-sign recognition
* Evaluate classification performance
* Analyze model errors
* Create an easy-to-use prediction interface
* Demonstrate a practical computer vision application

---

## 🔮 Future Improvements

Possible improvements include:

* 🎥 Real-time continuous sign recognition
* 🤟 Support for dynamic signs such as **J** and **Z**
* 🖐️ Hand detection and background removal
* 📱 Deployment as a mobile application
* ⚡ Real-time webcam prediction
* 🗣️ Converting detected letters into words or speech
* 📈 Improving performance using a larger and more diverse dataset

---

## 👨‍💻 Project Type

**Graduation Project — Computer Science / Artificial Intelligence**

### Main Area

```text
Computer Vision
        ↓
Image Classification
        ↓
Convolutional Neural Network
        ↓
ASL Letter Recognition
        ↓
Interactive Gradio Application
```

---

## 📜 License

This project is intended for educational and academic purposes.
