Batch Normalization in CNN on CIFAR-10

This project compares a simple CNN trained with and without Batch Normalization on the CIFAR-10 dataset.

The goal was to see whether BatchNorm actually improves training and final accuracy when everything else is kept the same.

Dataset

CIFAR-10 contains:

60,000 color images

10 classes

Image size: 32×32

Split:

50,000 training images

10,000 test images

Models Used
CNN without BatchNorm

Conv → ReLU → MaxPool
Conv → ReLU → MaxPool
FC → ReLU → Output

CNN with BatchNorm

Conv → BatchNorm → ReLU → MaxPool
Conv → BatchNorm → ReLU → MaxPool
FC → ReLU → Output

Training Setup

Framework: PyTorch

Optimizer: Adam

Learning rate: 0.001

Batch size: 128

Epochs: 10

Loss: CrossEntropyLoss

Results
Model	Test Accuracy
CNN without BatchNorm	71.08%
CNN with BatchNorm	70.46%
Observation

The BatchNorm model showed smoother training loss and slightly faster learning in the beginning.
But in this experiment, it did not give better final test accuracy.

Conclusion

Batch Normalization helped training become more stable, but it did not improve performance for this small CNN on CIFAR-10.

Takeaways

BatchNorm can improve training stability

It does not always improve final accuracy

Its effect may be more useful in deeper networks

Small experiments like this help understand how models actually behave
