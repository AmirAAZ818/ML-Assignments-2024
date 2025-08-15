# Noise Reduction with PCA and Autoencoders

## Overview

In this repository, noise reduction techniques using Principal Component Analysis (PCA) and Autoencoders on the `Fashion MNIST` dataset are analysed and also compared. The report explores the application of these methods to denoise grayscale clothing images, comparing their effectiveness through reconstruction errors and visualizations.

## Key Aspects

- **Dataset**: Fashion MNIST, with 70,000 grayscale 28×28 images (60,000 training, 10,000 test) across 10 clothing classes. Gaussian noise (mean=0, variance=1.0) was added to create noisy images.
  - Key Figure: ![Raw Dataset Sample]([./figs/fmn%20data%20raw.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Noise%20Reduction%20with%20PCA%20and%20Autoencoders/Assets/fmn%20data%20raw.png))
  - Key Figure: ![Noisy Dataset Sample]([./figs/fmn%20data%20noisy.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Noise%20Reduction%20with%20PCA%20and%20Autoencoders/Assets/fmn%20data%20noisy.png))
- **PCA**:
  - Linear dimensionality reduction to remove noise by retaining key components.
  - Optimal result with 80 principal components, achieving a reconstruction error of 0.0239.
  - Key Figure: ![Optimal PCA Components]([./figs/best%20k%20pca.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Noise%20Reduction%20with%20PCA%20and%20Autoencoders/Assets/best%20k%20pca.png))
- **Autoencoder**:
  - Neural network with Encoder (784→512→256→128) and Decoder (128→256→512→784) using `ReLU` activation.
  - Trained with learning rate=0.001, batch size=128, 25 epochs, achieving a reconstruction error of 0.013.
  - Key Figure: ![Autoencoder Train/Test Error]([./figs/train%20test%20error%20ae.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Noise%20Reduction%20with%20PCA%20and%20Autoencoders/Assets/train%20test%20error%20ae.png))
- **Results**:
  - Autoencoder outperforms PCA due to its ability to capture nonlinear relationships.
  - Key Figure: ![Comparison of Noise Reduction Methods]([./figs/resutl%20comparison.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Noise%20Reduction%20with%20PCA%20and%20Autoencoders/Assets/resutl%20comparison.png))
- **Fair Comparison**: Ensured fair comparison by adding noise once and using the same noisy dataset for both PCA (`Scikit-learn`) and Autoencoder `(PyTorch`).

## Libraries Used

The analysis was implemented in Python using:

- **NumPy**: For numerical operations and matrix computations (e.g., PCA eigenvector calculations).
- **Scikit-learn**: For PCA implementation and data preprocessing.
- **PyTorch**: For implementing and training the Autoencoder neural network.
- **Matplotlib**: For generating visualizations (e.g., error plots, image comparisons).
