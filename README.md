# Denoising-Autoencoder
This project focuses on image denoising of pistachio nut images using Convolutional Autoencoder and U-Net architectures.

### Business Context and Objective
In agricultural industries, image quality plays a critical role in automated inspection systems. High-resolution, clean images allow better feature extraction for identifying product defects or classifying quality grades. However, images captured in real-world environments are often noisy due to lighting variations, sensor limitations, or dust interference.
This project focuses on developing and comparing two deep learning approaches for denoising pistachio images:
- A basic convolutional autoencoder built from scratch.
- A fine-tuned U-Net architecture designed for improved feature retention and reconstruction accuracy.
The objective is to evaluate which model produces more visually faithful and structurally accurate reconstructions under noisy conditions.

### Key Steps in the Notebook
- Data Preparation: Loading and preprocessing noisy and clean pistachio images.
- Model 1 – Basic Autoencoder:
  1. Two Conv2D layers followed by MaxPooling2D for encoding.
  2. UpSampling2D and a final Conv2D layer for decoding.
  3. Designed to learn simple, low-level spatial patterns for basic denoising.
- Model 2 – Fine-Tuned U-Net:
  1. Custom-built U-Net from scratch.
  2. Encoder–decoder structure with skip connections for preserving spatial detail.
  3. Fine-tuned by adjusting neuron counts and learning rate.
  
Evaluation:
Measured using SSIM (Structural Similarity Index Measure) to assess the visual similarity between the denoised and original clean images.

SSIM (Structural Similarity Index Measure) is a perceptual metric that evaluates image similarity based on how humans perceive visual structure, contrast, and brightness.
- Range: 0 (completely different) to 1 (identical).
- Interpretation: Higher SSIM indicates the denoised image is visually and structurally closer to the original clean image.


### Results and Analysis 
The first model, the basic convolutional autoencoder, achieved an SSIM score of 0.81. It successfully reduced some of the noise but tended to blur the edges and lose fine texture information, resulting in smooth yet less detailed images.
The second model, the fine-tuned U-Net, significantly outperformed the autoencoder with an SSIM of 0.96. It produced visually sharp and structurally accurate reconstructions, effectively restoring both global appearance and local details.

Why the U-Net performed better:
- The skip connections in U-Net help recover fine-grained spatial information lost during downsampling.
- A deeper encoder-decoder allows the model to learn multi-scale contextual features.
- Fine-tuning with optimal neuron counts and learning rate improved convergence and reconstruction quality.

### Limitations
While the fine-tuned U-Net achieved excellent performance, some limitations remain:
- The dataset size and noise type were fixed — real-world noise might vary in intensity and distribution.
- The model’s effectiveness could drop under unseen lighting or texture conditions.
- Training U-Net from scratch is computationally expensive compared to transfer learning with pretrained encoders.

### Future Work
For future improvement, it is recommended to:
- Experiment with different noise distributions (Gaussian, speckle, motion blur) to improve model generalization.
- Incorporate data augmentation and transfer learning using pretrained backbones (e.g., ResNet or EfficientNet).
- Explore attention mechanisms (e.g., CBAM, SE blocks) within U-Net to enhance focus on important regions.
