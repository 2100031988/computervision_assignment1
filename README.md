# Image Classification Model Comparison

**FNN &nbsp;·&nbsp; VGG16 &nbsp;·&nbsp; ResNet18**

A comparative study of three neural network architectures — a **Feedforward Neural Network (FNN)**, **VGG16**, and **ResNet18** — evaluated on three benchmark image classification datasets: **MNIST**, **CIFAR-10**, and **CIFAR-100**.

---

## Overview

| | |
|---|---|
| **Models compared** | FNN, VGG16, ResNet18 |
| **Datasets used** | MNIST, CIFAR-10, CIFAR-100 |
| **Metrics tracked** | Accuracy, Precision, Recall, F1-score, Training Time |
| **Best overall model** | ResNet18 (highest mean accuracy) |
| **Highest single accuracy** | MNIST — 99.57% (ResNet18) |

---

## Models

### 1. Feedforward Neural Network (FNN)
A fully connected baseline network. Images are flattened into 1-D vectors before being passed through dense layers, so spatial relationships between pixels are not explicitly preserved.

$$h = f(Wx + b)$$

### 2. VGG16
A deep convolutional network that uses stacked 3×3 convolution filters to learn local spatial and hierarchical visual features.

$$Y(i,j) = \sum_{m}\sum_{n} W(m,n)\,X(i-m,\,j-n) + b$$

### 3. ResNet18
A convolutional network with **residual (skip) connections**, which help gradients propagate through deeper architectures and stabilize training.

$$y = F(x) + x$$

---

## Datasets

| Dataset | Classes | Image Type | Difficulty |
|---|---|---|---|
| **MNIST** | 10 | Grayscale digits | Low |
| **CIFAR-10** | 10 | Natural RGB images | Medium |
| **CIFAR-100** | 100 | Natural RGB images | High |

---

## Results Summary

### Accuracy (%) by Model and Dataset

| Model | MNIST | CIFAR-10 | CIFAR-100 | **Mean Accuracy** |
|---|---|---|---|---|
| FNN | 97.61 | 52.22 | 24.03 | 57.95 |
| VGG16 | 99.42 | **81.67** | 49.32 | 76.80 |
| **ResNet18** | **99.57** | 80.53 | **52.12** | **77.41** |

> **Accuracy was highest on MNIST across every model**, confirming it is the simplest of the three datasets. The best single result overall was **ResNet18 on MNIST at 99.57%**.

### Training Time (seconds)

| Model | MNIST | CIFAR-10 | CIFAR-100 | Mean Time |
|---|---|---|---|---|
| FNN | 153.12 | 141.46 | 142.04 | 145.54 |
| VGG16 | 553.84 | 445.08 | 431.21 | 476.71 |
| ResNet18 | 572.10 | 520.06 | 522.14 | 538.10 |

---

## Key Findings

- **MNIST is the easiest dataset** — all three models score above 97.6% accuracy on it, since digit images are simple and low-dimensional.
- **FNN degrades sharply on complex images** — accuracy drops from 97.61% (MNIST) to 52.22% (CIFAR-10) and 24.03% (CIFAR-100), because flattening images discards spatial structure.
- **VGG16 and ResNet18 stay far more robust** as image complexity increases, thanks to convolutional feature extraction.
- **ResNet18 wins overall** — highest mean accuracy (77.41%) and best result on the hardest dataset, CIFAR-100 (52.12%), due to residual connections improving gradient flow.
- **VGG16 is the more efficient runner-up** — nearly matches ResNet18's accuracy while training ~11% faster.

---

## Conclusion

| Rank | Model | Mean Accuracy | Notes |
|---|---|---|---|
| 1 | **ResNet18** | 77.41% | Best overall performance, strongest on CIFAR-100 |
| 2 | VGG16 | 76.80% | Close second, more time-efficient |
| 3 | FNN | 57.95% | Best only on MNIST; not suited for complex images |

**Recommendation:** Use **ResNet18** when accuracy is the top priority, **VGG16** when training/inference budget is limited, and **FNN** only as a lightweight baseline for simple, low-resolution tasks.

---

## Repository Structure

```
├── Q1_FNN.ipynb              # FNN implementation & results (MNIST, CIFAR-10, CIFAR-100)
├── Q2_VGG16.ipynb            # VGG16 implementation & results
├── Q3_ResNet18.ipynb         # ResNet18 implementation & results
├── Q4_Comparison.ipynb       # Final comparison notebook (this project)
└── README.md                 # Project overview (this file)
```

---

## Requirements

```
python >= 3.9
pandas
numpy
matplotlib
seaborn
```

Install with:
```bash
pip install pandas numpy matplotlib seaborn
```
