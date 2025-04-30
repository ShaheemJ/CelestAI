# CelestAI

## CelestAI Poster: 
![image](https://github.com/user-attachments/assets/f41138e3-654d-4f68-96f0-0055ff84319a)


**CelestAI: Improving Astronomical Phenomena Detection with Generative AI**

**Authors:** Hrishikesh Naveenam, Shaheem Jaleel, Karthik Yammanur, Samarth Bikki, Lindsay King, Jagadeep Kalluri

---

## Table of Contents
1. [Introduction](#introduction)
2. [Dataset and Experimental Setup](#dataset-and-experimental-setup)
3. [Model Architectures](#model-architectures)
4. [Results](#results)
5. [Analysis](#analysis)
6. [Conclusion](#conclusion)
7. [Repository Structure](#repository-structure)
8. [Getting Started](#getting-started)
9. [References](#references)

---

## Introduction
Astronomy’s rarest and most elusive phenomena—such as gravitational lensing, kilonovae, and fast radio bursts—hold profound clues about the universe’s fundamental mysteries. However, their infrequent occurrence limits observational opportunities and hampers scientific analysis. **CelestAI** addresses this gap by leveraging Generative AI to synthesize highly realistic astronomical images, augmenting existing datasets and enhancing the performance of rare-event detection models.

## Dataset and Experimental Setup
- **Dataset:** Galaxy10 DECals, an enhanced version of Galaxy10, comprising 17,736 colored galaxy images (256×256 px in g, r, z bands) labeled by Galaxy Zoo volunteers into 10 morphological classes.
- **Morphological Classes (10):** Disturbed, Merging, Round Smooth, In-between Round Smooth, Cigar Shaped Smooth, Barred Spiral, Unbarred Tight Spiral, Unbarred Loose Spiral, Edge-on without Bulge, Edge-on with Bulge.
- **Class Distribution:** Ranges from 334 to 2,645 images per category.
- **Augmentation Strategy:** 200 synthetic images (20% of the real data) were generated per model and merged with 1,000 real images to form an augmented training set.

## Model Architectures
1. **DCGAN (Deep Convolutional GAN):** Utilizes strided convolutions and batch normalization to generate realistic images from random latent vectors.  
2. **StyleGAN (Transfer Learning):** Fine-tuned from pre-trained weights to leverage style priors, enabling high-fidelity synthesis with few target-domain examples.  
3. **VAE (Variational Autoencoder):** Encoder–decoder framework trained with a KL-divergence regularized loss to learn a continuous latent distribution.  
4. **VQGAN (Vector-Quantized GAN):** Combines discrete codebook quantization with adversarial and perceptual losses for sharp, detailed image generation while maintaining a compact latent space.  

## Results
| Model    | Recall | F1 Score | ROC-AUC |
|----------|:------:|:--------:|:-------:|
| Baseline |  0.57  |   0.67   |  0.75   |
| VQGAN    |  0.62  |   0.72   |  0.78   |
| VAE      |  0.65  |   0.73   |  0.79   |
| StyleGAN |  0.68  |   0.75   |  0.81   |
| **DCGAN**|**0.72**|**0.79**  |**0.85** |

## Analysis
- **Quality vs. Efficiency:** VQGAN provides the best balance between detection performance and computational cost, achieving solid Recall and F1 gains with moderate resource use.  
- **Metric Comparison:** While DCGAN achieves the highest overall detection metrics, StyleGAN’s strong Recall and ROC-AUC indicate effective transfer learning from large-scale pre-trained models.  
- **Detection Improvements:** DCGAN’s 0.72 Recall (15% improvement over baseline) highlights the impact of GAN-based augmentation on rare event detection.  

## Conclusion
CelestAI demonstrates that generative models can overcome data scarcity in astronomical research by synthesizing high-quality images that boost detection performance. Among the evaluated architectures, DCGAN delivers the optimal trade-off between image fidelity and model efficiency, significantly enhancing rare-phenomena detection capabilities.

CelestAI is published by ACM Research, a registered student organization. CelestAI is not an official publication of UT Dallas.
