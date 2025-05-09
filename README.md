This is the official repo for

**OmiAD: One-Step Adaptive Masked Diffusion Model for Multi-class Anomaly Detection via Adversarial Distillation (ICML 2025)**

## Abstract
Diffusion models have demonstrated outstanding performance in industrial anomaly detection. However, their iterative denoising nature results in slow inference speed, limiting their practicality for real-time industrial deployment. To address this challenge, we propose OmiAD, a one-step masked diffusion model for multi-class anomaly detection, derived from a well-designed multi-step **A**daptive **M**asked **D**iffusion **M**odel (AMDM) and compressed using **A**dversarial **S**core **D**istillation (ASD). OmiAD first introduces AMDM, equipped with an adaptive masking strategy that dynamically adjusts masking patterns based on noise levels and encourages the model to reconstruct anomalies as normal counterparts by leveraging broader context, to reduce the pixel-level shortcut reliance. Then, ASD  is developed to compress the multi-step diffusion process into a single-step generator by score distillation and incorporating a shared-weight discriminator effectively reusing parameters while significantly improving both inference efficiency and detection performance. The effectiveness of OmiAD is validated on four diverse datasets, achieving state-of-the-art performance across seven metrics while delivering a remarkable inference speedup.

## Overview of the ASD framework
![image](https://github.com/user-attachments/assets/545ac28e-2dba-41e2-b184-4452313a92d5)

## Quantitative Results on different AD datasets for multi-class setting
![image](https://github.com/user-attachments/assets/2c452ee4-1566-435b-bdca-b717287440e6)

## Algorithm for Adversarial Score Distillation in OmiAD
![image](https://github.com/user-attachments/assets/1acf69fe-e569-4eba-a1b4-fb16bff54e3d)


## Quick Start


## Acknowledgement
This code is primarily based on modifications made from [guided-diffusion
](https://github.com/openai/guided-diffusion), [SiD](https://github.com/mingyuanzhou/SiD) and [UniAD](https://github.com/zhiyuanyou/UniAD). We would like to express our gratitude to the authors of these repositories for their excellent foundational work, which significantly inspired and supported our research. Their contributions have been invaluable in the development of this project.



