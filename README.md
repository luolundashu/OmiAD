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



