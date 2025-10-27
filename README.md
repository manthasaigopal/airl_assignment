# Q1: Vision Transformer (ViT) from Scratch on CIFAR-10

This project implements a Vision Transformer (ViT) trained from scratch on the CIFAR-10 dataset using PyTorch.  
The goal was to explore how transformer-based architectures perform on small-scale image classification without pretraining.


## How to Run

Simply open the provided Colab notebook and run all cells in order. All dependencies are installed automatically within the notebook.

## Abalation Study

| img_size | patch_size | patch_overlap | embed_dim | num_heads | depth | dropout | mlp_dim | Train Accuracy | Test Accuracy |
|-----------|-------------|----------------|------------|------------|--------|----------|----------|----------------|---------------|
| 32        | 4           | No             | 64         | 4          | 4      | 0.1      | 128      | 12.87          | 19.93         |
| 224       | 16          | No             | 64         | 4          | 6      | 0.1      | 128      | 95.00          | 77.42         |
| 224       | 16          | No             | 128        | 4          | 6      | 0.2      | 256      | 90.62          | 78.44         |
| 224       | 16          | Yes            | 128        | 4          | 6      | 0.2      | 256      | 96.40          | 81.33         |
| 224       | 16          | Yes            | 128        | 4          | 4      | 0.5      | 256      | 91.11          | **83.24**     |
