# Batch Normalization Experiment on CNN (CIFAR-10)

## Overview

Batch Normalization is a widely used technique in deep learning that is often said to stabilize training and improve convergence. Instead of just accepting that claim, I wanted to test it myself in a controlled experiment.

In this project, I trained the **same CNN architecture with and without Batch Normalization** on the CIFAR-10 dataset and compared how the training process behaved.

The goal was not only to compare final accuracy, but also to observe **how the training dynamics change when BatchNorm is introduced.**

---

## Dataset

The experiment uses the **CIFAR-10 dataset**, which contains:

- 60,000 color images
- Image size: 32 × 32
- 10 object classes

Classes include:

- airplane
- automobile
- bird
- cat
- deer
- dog
- frog
- horse
- ship
- truck

The dataset is split into:

- **50,000 training images**
- **10,000 test images**

I chose CIFAR-10 because it is small enough to train quickly but still complex enough to observe differences in model behavior.

---

## Experiment Design

To make the comparison fair, both models use the **same architecture and training setup**.

The only difference between them is whether **Batch Normalization layers are used**.

### Model A — Baseline CNN (No BatchNorm)

Architecture:

Conv → ReLU → MaxPool  
Conv → ReLU → MaxPool  
Fully Connected → ReLU → Output

---

### Model B — CNN with BatchNorm

Architecture:

Conv → BatchNorm → ReLU → MaxPool  
Conv → BatchNorm → ReLU → MaxPool  
Fully Connected → ReLU → Output

Everything else remained identical:

- same dataset
- same optimizer
- same learning rate
- same number of epochs

This ensures that any observed difference comes specifically from Batch Normalization.

---

## Training Setup

Framework: **PyTorch**

Training configuration:

- Optimizer: Adam
- Learning rate: 0.001
- Batch size: 128
- Epochs: 10
- Loss function: CrossEntropyLoss

Both models were trained under the same conditions.

---

## Results

### Test Accuracy

| Model | Accuracy |
|------|------|
| CNN without BatchNorm | **71.08%** |
| CNN with BatchNorm | **70.46%** |

Interestingly, the model **without BatchNorm achieved slightly higher test accuracy** in this experiment.

---

### Training Loss Curves

The training curves show how the loss evolved during training.

![Training Curve](training_curve.png)

From the graph, the model with BatchNorm shows **smoother and slightly faster loss reduction** during early training epochs.

---

## Observations

A few interesting things stood out:

- The BatchNorm model reduced training loss more smoothly.
- The difference in loss appears mainly during **early epochs**.
- However, the improvement in optimization did **not translate into higher final test accuracy**.

This suggests that BatchNorm helped **training stability**, but in this small CNN architecture it did not significantly improve final performance.

---

## Where BatchNorm Didn’t Help

In this experiment, Batch Normalization did not improve test accuracy and actually performed slightly worse.

A possible explanation is that the network used here is relatively shallow. BatchNorm tends to have stronger benefits in **deeper networks**, where training becomes more unstable.

Since the architecture here is simple, the optimization problem may already be easy enough that BatchNorm does not provide a large advantage.

---

## What I Learned

This experiment reinforced an important point:  

Batch Normalization mainly improves **training stability and convergence speed**, but it does not always guarantee better final accuracy.

Its impact likely depends on:

- network depth
- dataset complexity
- training duration

---

## Future Experiments

If I extended this experiment further, I would try:

1. Training a **deeper CNN architecture**
2. Running training for **more epochs**
3. Testing the same setup on a different dataset

This could help determine when BatchNorm becomes more beneficial.

## How to Reproduce the Experiment

1. Open the notebook in **Google Colab**
2. Run all cells
3. CIFAR-10 will download automatically
4. Both models will train and generate the training curves

---

## Final Thoughts

The main takeaway from this experiment is that widely used techniques like Batch Normalization are worth testing and understanding rather than simply applying blindly. Even simple experiments can reveal interesting insights about how neural networks actually learn.
