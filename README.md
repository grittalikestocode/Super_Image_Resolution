# Comparative Analysis of Image Super-Resolution Models

A comprehensive analysis of three deep learning models for image super-resolution (SR): Enhanced Deep Super-Resolution (EDSR), Very Deep Super-Resolution (VDSR), and Deep Recursive Convolutional Network (DRCN).

## Overview

This project compares the performance of three popular super-resolution architectures with different design philosophies:
- **EDSR**: A deep residual network architecture with 32 convolutional layers
- **VDSR**: A deep network with 20 convolutional layers focused on residual learning
- **DRCN**: A recursive architecture that leverages weight sharing across layers

## Dataset

- **Training**: DIV2K dataset (800 training, 100 validation images in 2K resolution)
- **Testing**: Set5 benchmark dataset

## Model Architectures

### EDSR
- Deep residual network with 32 convolutional layers
- Uses MeanShift layer for input normalization
- Includes multiple Residual Blocks with ReLU activations
- Employs pixel shuffling for upsampling

### VDSR
- 20 convolutional layers with 64 channels each
- Global skip connection for residual learning
- ReLU activation after each convolutional layer (except final output)
- Trained using L2 loss

### DRCN
- Embedding network with two convolutional layers
- Recursive inference network that applies the same convolutional layers multiple times
- Reconstruction network that combines recursive outputs
- Custom loss function combining MSE, color loss, recursive loss, and L2 regularization

## Training Setup

| Model | Image Size (HR/LR) | Loss Function | Optimizer | Learning Rate | Epochs |
|-------|-------------------|--------------|-----------|---------------|--------|
| EDSR  | 512x512 / 128x128 | L1 Loss      | Adam      | 0.0001        | 20     |
| VDSR  | 128x128 / 64x64   | L2 Loss      | SGD       | 0.001         | 50     |
| DRCN  | 512x512 / 128x128 | Custom       | Adam      | 0.0006        | 70     |

## Results

### Image Quality Metrics

| Model | PSNR  | SSIM   | Perceptual Index (PI) |
|-------|-------|--------|------------------------|
| EDSR  | 30.14 | 0.8666 | -5.5048                |
| VDSR  | 29.82 | 0.9574 | -5.3873                |
| DRCN  | 31.86 | 0.8876 | -10.3662               |

### Computational Efficiency

| Model | Parameters | Inference Time (ms) | Memory Usage (MB) |
|-------|------------|---------------------|-------------------|
| EDSR  | 43,089,923 | 4126.71             | 512.48            |
| VDSR  | 668,227    | 136.63              | 6.02              |
| DRCN  | 1,888,148  | 101.54              | 0.21              |

## Key Findings

- **DRCN** demonstrates the highest PSNR, indicating strong reconstruction capabilities, with excellent efficiency for real-time applications
- **VDSR** achieves the highest SSIM and good PI scores, balancing structural and perceptual quality with reasonable computational demands
- **EDSR** provides balanced reconstruction quality but requires more computational resources

## Future Work

- Explore hybrid approaches combining strengths of multiple architectures
- Improve training techniques for faster convergence
- Adapt models to diverse datasets for broader applications

## Installation and Usage

```bash
# Clone the repository
git clone https://github.com/Lynn00Chen/image-resolution.git

cd image-super-resolution-comparison

```
