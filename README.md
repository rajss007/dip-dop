# MNIST Handwritten Digit Recognition

## Description


This project is a handwritten-digit recognition system built with **Keras and TensorFlow** using the **MNIST dataset**.

The project trains a convolutional neural network (CNN) to classify grayscale handwritten digit images into one of the ten classes **0–9**. The training pipeline:

- Loads the MNIST training dataset.
- Removes corrupted and completely blank images.
- Applies random-rotation data augmentation during training.
- Builds a CNN using convolutional, separable-convolutional, batch-normalization, residual, pooling, and dropout layers.
- Trains the model for 2 epochs.
- Saves the trained model as `mnist_model.keras`.

The project also provides scripts for evaluating the model on the MNIST test set and for predicting a digit from an individual image.

The trained model expects images representing handwritten digits and resizes input images to **28 × 28 pixels** in grayscale before prediction.

---

## Task

The task is to develop and evaluate a machine-learning model capable of recognizing handwritten digits.

Given an input image containing a handwritten digit, the model:

1. Loads the image.
2. Converts it to grayscale.
3. Resizes it to 28 × 28 pixels.
4. Passes it through the trained MNIST model.
5. Computes class probabilities using softmax.
6. Selects the digit with the highest probability.
7. Displays the predicted digit and its confidence.

The individual-image evaluation script performs these steps automatically. It loads `mnist_model.keras`, asks the user for an image path, predicts the digit, and displays the image with the prediction and confidence. 

---

## Prerequisites

Before running the project, install:

- **Python 3.x**
- `pip`
- A system capable of installing TensorFlow/Keras and their dependencies
- The project files listed in the [Project Structure](#project-structure) section

The required Python packages and their pinned versions are provided in `requirements.txt`. The project currently specifies Keras 3.15.1, NumPy 2.5.3, Matplotlib 3.11.2, and TensorFlow 2.22.0rc0, among other dependencies.

---

## Installation

### 1. Clone or download the project

Place all project files in a single project directory.

Example:

```text
mnist-digit-recognition/
```

### 2. Create a virtual environment (recommended)

On Windows:

```bash
python -m venv venv
venv\Scripts\activate
```

On Linux/macOS:

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install the dependencies

Run:

```bash
pip install -r requirements.txt
```

The supplied `requirements.txt` contains the complete pinned dependency list for the project.

---

## Configuration

There is no separate configuration file required.

The main configuration values are defined directly in the Python scripts.

### Model configuration

The model uses:

- Input shape: `28 × 28 × 1`
- Number of classes: `10`
- Optimizer: Adam
- Learning rate: `0.001`
- Loss: Sparse Categorical Crossentropy with logits
- Batch size: `64`
- Training epochs: `2`
- Data augmentation: random rotation
- Dropout: `0.25`

The model is saved as:

```text
mnist_model.keras
```

### Input image configuration

For individual-image prediction, the input image is automatically:

- Loaded as grayscale.
- Resized to `28 × 28`.
- Converted to an array.
- Expanded to the required batch format.

Therefore, the source image does not have to already be 28 × 28 pixels, although using a clear handwritten digit image is recommended.

---

## Usage

### 1. Train the model

Run:

```bash
python train.py
```

The training script downloads/loads the MNIST dataset, removes invalid and blank images, trains the CNN, and saves the resulting model as:

```text
mnist_model.keras
```

The training pipeline uses a batch size of 64 and trains for 2 epochs.

---

### 2. Evaluate the model on the MNIST test set

Run:

```bash
python test.py
```

This script:

1. Loads the MNIST test set.
2. Removes corrupted and completely blank images.
3. Loads `mnist_model.keras`.
4. Predicts all cleaned test images.
5. Calculates test accuracy.
6. Generates and displays a 10 × 10 confusion matrix.

The confusion matrix uses:

- **Rows** = true labels
- **Columns** = predicted labels

The script also displays the numerical value inside each confusion-matrix cell.

---

### 3. Predict a digit from an individual image

Run:

```bash
python evaluating.py
```

The program will prompt:

```text
Enter image file path:
```

Enter the path of an image containing a handwritten digit.

For example, if the project contains an `image` folder:

```text
image\0.png
```

You can use the images in the `image` folder by entering their locations in this form:

```text
image\filename.png
```

For example:

```text
image\0.png
image\00.png
image\1.png
image\11.png
...
image\9.png
image\99.png
```

You may also provide the **full path of any other image of your choice**, for example:

```text
C:\path\to\your\digit.png
```

The script loads the image, converts it to grayscale, resizes it to 28 × 28, predicts the digit, and prints:

```text
Predicted digit: X
Confidence: Y %
```

It then displays the input image together with the prediction and confidence.

---

## Testing

There are two main ways to test the project.

### A. Test the model on the MNIST test dataset

Run:

```bash
python test.py
```

This is the dataset-level evaluation. It reports the model's test accuracy and displays a confusion matrix.

The test script filters the original MNIST test data to remove non-finite and completely blank images before evaluating the model.

### B. Test individual images

Run:

```bash
python evaluating.py
```

When prompted for the image path, use an image from the project's `image` folder:

```text
image\0.png
```

or:

```text
image\00.png
```

You can test the other supplied images in the same way:

```text
image\1.png
image\11.png
image\2.png
image\22.png
...
image\9.png
image\99.png
```

You can also test with any other suitable handwritten-digit image by providing its full file path.

### Expected input

The model is designed for handwritten digits similar to the MNIST dataset:

- One digit per image.
- Grayscale input.
- Clear digit shape.
- Preferably a digit centered similarly to MNIST images.

The prediction script handles grayscale conversion and resizing automatically.

---

## Evaluation Workflow

A typical workflow is:

```text
1. Install dependencies
       ↓
2. Train model
       ↓
3. mnist_model.keras is created
       ↓
4. Run test.py
       ↓
5. Check test accuracy and confusion matrix
       ↓
6. Run evaluating.py
       ↓
7. Enter an image path
       ↓
8. Check predicted digit and confidence
```

If `mnist_model.keras` is already available, training can be skipped and the existing model can be used directly for testing and individual-image evaluation.

---

## API / Documentation Links

The project is based primarily on Python, TensorFlow, Keras, NumPy, Matplotlib, and the TensorFlow/Keras MNIST dataset.

- **Python:** https://www.python.org/doc/
- **TensorFlow:** https://www.tensorflow.org/api_docs
- **Keras:** https://keras.io/api/
- **Keras image utilities:** https://keras.io/api/utils/image_utils/
- **TensorFlow MNIST dataset:** https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist
- **NumPy:** https://numpy.org/doc/
- **Matplotlib:** https://matplotlib.org/stable/api/

---

## Project Structure

A recommended project layout is:

```text
.
├── image/
│   ├── 0.png
│   ├── 00.png
│   ├── 1.png
│   ├── 11.png
│   ├── ...
│   ├── 9.png
│   └── 99.png
├── train.py
├── test.py
├── evaluating.py
├── mnist_model.keras
├── requirements.txt
└── README.md
```

### File descriptions

| File / Directory | Purpose |
|---|---|
| `train.py` | Loads and cleans MNIST training data, builds and trains the CNN, and saves the trained model. |
| `test.py` | Evaluates the saved model on the MNIST test set and generates a confusion matrix. |
| `evaluating.py` | Predicts a digit from a user-provided image path and displays the prediction/confidence. |
| `mnist_model.keras` | Saved trained Keras model used for evaluation and prediction. |
| `requirements.txt` | Pinned Python dependencies required by the project. |
| `image/` | Contains example images that can be supplied to `evaluating.py`. |
| `README.md` | Project documentation and usage instructions. |

---

## Model Architecture

The model is a CNN designed for 28 × 28 grayscale MNIST images.

The architecture includes:

1. Input layer for `(28, 28, 1)`.
2. Rescaling of pixel values by `1/255`.
3. Initial convolution and batch normalization.
4. ReLU activation.
5. Multiple blocks containing:
   - ReLU activation
   - Separable convolution
   - Batch normalization
   - Max pooling
   - Residual projection and addition
6. A final separable convolution block.
7. Global average pooling.
8. Dropout.
9. A dense output layer with 10 classes.

The training script uses Adam with a learning rate of `1e-3` and sparse categorical crossentropy from logits.

---

## Data Cleaning and Augmentation

The training and test pipelines remove:

- Images containing non-finite values.
- Completely blank images.

For training, random rotation is used as data augmentation. This helps expose the model to small variations in the orientation of handwritten digits.

The training dataset is shuffled, batched, augmented, and prefetched before model training.

---

## Output

### Training

Successful training produces:

```text
mnist_model.keras
```

### Test evaluation

`test.py` prints the cleaned dataset size and the final test accuracy, then displays the confusion matrix.

### Individual prediction

`evaluating.py` prints the predicted digit and confidence and displays the image with the prediction.

Example output format:

```text
Predicted digit: 7
Confidence: 98.52 %
```

The exact prediction and confidence depend on the supplied image and the trained model.

---

## Troubleshooting

### `FileNotFoundError` for `mnist_model.keras`

Make sure the model file exists in the current working directory:

```text
mnist_model.keras
```

If it does not exist, train the model first:

```bash
python train.py
```

### Image cannot be loaded

Check that the path supplied to `evaluating.py` is correct.

For an image in the project folder, use:

```text
image\filename.png
```

Alternatively, provide the complete path to the image.

### Dependency installation problems

Make sure you are using a compatible Python environment and install the exact dependencies with:

```bash
pip install -r requirements.txt
```

Using a virtual environment is recommended to avoid conflicts with packages installed globally.

---

## Credits / Authors

**Author:** Project author / repository owner

This project uses the publicly available **MNIST handwritten digit dataset** through the TensorFlow/Keras dataset API and relies on the TensorFlow, Keras, NumPy, and Matplotlib libraries.

---

## License

No explicit project license was provided in the supplied project files.

If this project is intended for public distribution, add an appropriate license file such as `LICENSE` and update this section with the selected license and its terms.

---

## Quick Start

For the shortest setup-to-test workflow:

```bash
# Install dependencies
pip install -r requirements.txt

# Train the model (skip if mnist_model.keras already exists)
python train.py

# Evaluate on the MNIST test set
python test.py

# Predict an individual image
python evaluating.py
```

When `evaluating.py` asks for an image path, an image from the project's `image` folder can be supplied as:

```text
image\0.png
```

or:

```text
image\00.png
```

and similarly for the other supplied images (`1.png`, `11.png`, ..., `9.png`, `99.png`). You may also provide the full path of another image of your choice for testing.
