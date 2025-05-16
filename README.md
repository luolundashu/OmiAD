This is the official repo for

**OmiAD: One-Step Adaptive Masked Diffusion Model for Multi-class Anomaly Detection via Adversarial Distillation (ICML 2025)**

## Abstract
Diffusion models have demonstrated outstanding performance in industrial anomaly detection. However, their iterative denoising nature results in slow inference speed, limiting their practicality for real-time industrial deployment. To address this challenge, we propose OmiAD, a one-step masked diffusion model for multi-class anomaly detection, derived from a well-designed multi-step **A**daptive **M**asked **D**iffusion **M**odel (AMDM) and compressed using **A**dversarial **S**core **D**istillation (ASD). OmiAD first introduces AMDM, equipped with an adaptive masking strategy that dynamically adjusts masking patterns based on noise levels and encourages the model to reconstruct anomalies as normal counterparts by leveraging broader context, to reduce the pixel-level shortcut reliance. Then, ASD  is developed to compress the multi-step diffusion process into a single-step generator by score distillation and incorporating a shared-weight discriminator effectively reusing parameters while significantly improving both inference efficiency and detection performance. The effectiveness of OmiAD is validated on four diverse datasets, achieving state-of-the-art performance across seven metrics while delivering a remarkable inference speedup.

## 1. Qualitative comparison of pixel-level anomaly segmentation results across four datasets. From left to right: normal sample as the reference, anomaly sample, ground truth (GT), predicted anomaly maps by UniAD, HVQ-Trans, DiAD, and ours.
![image](https://github.com/user-attachments/assets/8f1593d2-2800-4ee4-a80d-2bb002e28459)

## 2. Overview of the ASD framework
![image](https://github.com/user-attachments/assets/545ac28e-2dba-41e2-b184-4452313a92d5)

## 3. Quantitative Results on different AD datasets for multi-class setting
![image](https://github.com/user-attachments/assets/2c452ee4-1566-435b-bdca-b717287440e6)

### Table 1: Quantitative Results on Different AD Datasets for Multi-class Setting

| Dataset   | Method        | \multicolumn{3}{c|}{Image-level}     | \multicolumn{4}{c|}{Pixel-level}            | mAD  |
|-----------|---------------|--------|------|--------|--------|------|--------|--------|------|
|           |               | AU-ROC | AP   | F1_max | AU-ROC | AP   | F1_max | AU-PRO |      |
| **MVTec-AD** | RD4AD        | 94.6   | 96.5 | 95.2   | 96.1   | 48.6 | 53.8   | 91.1   | 82.3 |
|           | UniAD         | 96.5   | 98.8 | 96.2   | 96.8   | 43.4 | 49.5   | 90.7   | 81.7 |
|           | SimpleNet     | 95.3   | 98.6 | 95.8   | 96.9   | 45.9 | 49.7   | 86.5   | 81.2 |
|           | DeSTSeg       | 89.2   | 95.5 | 91.6   | 93.1   | **54.3** | 50.9 | 64.8   | 77.1 |
|           | DiAD          | 97.2   | 99.0 | 96.5   | 96.8   | 52.6 | 55.5   | 90.7   | 84.0 |
|           | HVQ-Trans     | 98.0   | 99.5 | 97.5   | 97.3   | 48.2 | 53.3   | 91.4   | 83.8 |
|           | **AMDM (Ours)** | 98.4 | 99.0 | 97.4   | 97.5   | 51.5 | 56.1   | 92.6   | 84.6 |
|           | **OmiAD (Ours)** | **98.8** | **99.7** | **98.5** | **97.7** | 52.6 | **56.7** | **93.2** | **85.3** |

| **VisA**    | RD4AD        | 92.4   | 92.4 | 89.6   | 98.1   | 38.0 | 42.6   | **91.8** | 77.8 |
|           | UniAD         | 88.8   | 90.8 | 85.8   | 98.3   | 33.7 | 39.0   | 85.5   | 74.6 |
|           | SimpleNet     | 87.2   | 87.0 | 81.8   | 96.8   | 34.7 | 37.8   | 81.4   | 72.4 |
|           | DeSTSeg       | 88.9   | 89.0 | 85.2   | 96.1   | 39.6 | **43.4** | 67.4 | 72.8 |
|           | DiAD          | 86.8   | 88.3 | 85.1   | 96.0   | 26.1 | 33.0   | 75.2   | 70.1 |
|           | HVQ-Trans     | 93.2   | 92.8 | 87.6   | 97.6   | 39.8 | 39.6   | 86.3   | 76.2 |
|           | **AMDM (Ours)** | 94.8 | 95.6 | 91.1   | 98.7   | 39.8 | 43.5   | 88.4   | 78.9 |
|           | **OmiAD (Ours)** | **95.3** | **96.0** | **91.2** | **98.9** | **40.4** | 44.1 | 89.2 | **79.3** |

| **MPDD**    | RD4AD        | 84.1   | 83.2 | 84.1   | 98.1   | 35.2 | 38.7   | 93.4   | 73.8 |
|           | UniAD         | 82.2   | 87.1 | 85.1   | 95.1   | 18.9 | 25.0   | 81.0   | 67.9 |
|           | SimpleNet     | 90.6   | 94.1 | 89.7   | 97.1   | 33.6 | 35.7   | 90.0   | 75.8 |
|           | DeSTSeg       | 93.0   | 95.1 | 90.6   | 94.1   | 33.2 | 37.6   | 59.8   | 71.9 |
|           | DiAD          | 74.6   | 82.1 | 82.5   | 93.5   | 15.9 | 21.2   | 78.4   | 64.0 |
|           | HVQ-Trans     | 86.5   | 88.1 | 85.8   | 96.7   | 27.6 | 31.4   | 86.9   | 71.9 |
|           | **AMDM (Ours)** | 93.3 | 94.9 | 90.7   | 98.4   | 41.6 | 42.3   | **94.5** | 78.4 |
|           | **OmiAD (Ours)** | **93.7** | **95.5** | **90.9** | **98.6** | **37.6** | **42.3** | 94.0 | **78.9** |

| **Real-IAD** | RD4AD       | 82.4   | 79.0 | 73.9   | 97.3   | 25.0 | 32.7   | 89.6   | 68.6 |
|           | UniAD         | 83.0   | 80.9 | 74.3   | 97.3   | 21.1 | 29.2   | 86.7   | 67.5 |
|           | SimpleNet     | 57.2   | 53.4 | 61.5   | 75.2   | 2.8  | 6.5    | 39.0   | 42.3 |
|           | DeSTSeg       | 82.3   | 79.2 | 73.2   | 94.6   | **37.9** | **41.7** | 40.6 | 64.2 |
|           | DiAD          | 75.6   | 66.4 | 69.9   | 88.0   | 2.9  | 7.1    | 58.1   | 52.6 |
|           | HVQ-Trans     | 86.6   | 89.4 | 77.8   | 97.6   | 30.7 | 33.7   | 87.2   | 72.6 |
|           | **AMDM (Ours)** | 89.8 | 87.7 | 81.9   | 98.6   | 36.5 | 41.4   | **92.6** | 75.5 |
|           | **OmiAD (Ours)** | **90.1** | **88.6** | **82.8** | **98.9** | 37.7 | 42.6 | 93.1 | **76.3** |

## 4. Quick Start
**4.1 Datasets**
- **Create the dataset directory**. The datasets can be downloaded from [MVTec-AD](https://www.mvtec.com/company/research/datasets/mvtec-ad/), [VisA](https://github.com/amazon-science/spot-diff), [MPDD](https://github.com/stepanje/MPDD), [RealIAD](https://github.com/Tencent/AnomalyDetection_Real-IAD](https://realiad4ad.github.io/Real-IAD/)).  Unzip the file and move some to `./my_data/MVTec-AD/`. To ensure consistency across datasets, please run `make_visa_dataset.py` and `make_realiad_dataset.py` to convert the VisA and RealAd datasets into the same format as MVTec-AD and MPDD.

**4.2 Training**
- **Generate dataset JSON files** Run `make_json.py` inside the `./data/` directory to generate the dataset JSON files.

- **Train the AMDM model:** Run `train_AMDM.py` inside the `./main/` directory to train the AMDM model.

- **Train the OmiAD:** Run `train_OmiAD.py` inside the `./main/` directory to train the OmiAD model. Make sure to set `args.e = False`.

**4.3 Testing**

- **Test the OmiAD:** Run `train_OmiAD.py` inside the `./main/` directory to train the OmiAD model. Make sure to set `args.e = True`.

- **Noting:**
We have also released our well-trained checkpoint on MVTec,VisA,MPDD,RealIAD at: ------, Extract code：-----. It is free to download the checkpoint and put it at `\experiments\MVTec-AD\G_checkpoints\G_ckpt_best.pth.tar`

**4.4 Visualize Reconstructed Features**
- **Train Decoders for Visualization:** Run `train_decoder.py` inside the `./main/` directory to train decoder. 

- **Visualize Reconstructed Features:** Run `vis_rec.py` inside the `./main/` directory to Visualize Reconstructed Features.

    **Note:** Please make sure **args.make_npy** is set to True when running `train_OmiAD.py` beforehand.


## 5. Welcome to discuss with us (fengyx@stu.xidian.edu.cn) and cite our paper:
OmiAD: One-Step Adaptive Masked Diffusion Model for Multi-class Anomaly Detection via Adversarial Distillation

## 6. Acknowledgement
This code is primarily based on modifications made from [guided-diffusion
](https://github.com/openai/guided-diffusion), [SiD](https://github.com/mingyuanzhou/SiD) and [UniAD](https://github.com/zhiyuanyou/UniAD). We would like to express our gratitude to the authors of these repositories for their excellent foundational work, which significantly inspired and supported our research. Their contributions have been invaluable in the development of this project.



