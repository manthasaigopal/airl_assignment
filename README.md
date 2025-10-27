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

## Discussion
The ablation study revealed that increasing the input resolution from (32 x 32) to (224 x 224) substantially improves accuracy, indicating that a higher token count allows self-attention to capture richer spatial dependencies. Expanding the embedding and MLP dimensions enhanced generalization by increasing representational capacity of the model. The introduction of overlapping patches yields the largest gain. This suggests that local spatial continuity is crucial when training from scratch on limited data. Since earlier experiments revealed that the model was overfitting (train accuracy around 95% but test only around 77%) in the subsequent experiment, I reduced the number of encoder stacks to 4 and increased droput regularization setting p=0.5. Overall, the study shows that controlled capacity scaling, local overlap, and strong regularization are key to stable and high performing ViT training in low data regimes.


# Q2: Text-Driven Image Segmentation with SAM 2

The user can upload an image and also provide a text prompt along with the image. The image along with the prompt is fed to OWL-ViT Model in order to obtain bounding box coordinates. These bounding box coordinates are then used as prompts to SAM 2 model in order to obtain a fine grained segmentation mask. Below is an example of user input image and text prompt. 

![Input Image](https://ultralytics.com/images/zidane.jpg)

Below is the output from the OWL-ViT Model. 

Output1

Above bounding boxes are given as prompts to the SAM 2 Model and the final result is shown below. 

Output2
