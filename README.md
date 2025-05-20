<div align="center">
 
 <h1> 🔥  Forest_Fire_and_Smoke_Detection  💨</h1>
</div>
<p align="center">
<strong>DSBA 6165: AI and Deep Learning</strong><br> 
<strong>Submitted by:</strong> Sravani Kuncham, Farah Naz  <br>
<strong>Instructor:</strong> Archit Parnami  
</p>
<p align="center">
  📄 <a href= "DSBA_6165_Final_Report.pdf"> Final Report</a> | 🖥️ <a href = "Final%20Project%20Presentation%20Incremental%20Deep%20Learning%20for%20Fire,%20Smoke%20and%20Haze%20Detection.pdf">Presentation</a>
 </p>                                                 

## 🔍 Project Overview
This project applies **Learning without Forgetting (LwF)** to the problem of wildfire classification. We extend a pre-trained deep learning model to learn a new class (haze) without forgetting previously learned classes (fire, nofire, smoke, smokefire)

<p align="center">
<img width="800" height="400" src="https://github.com/sravanikuncham466/DSBA_6165_Forest_Fire_and_Smoke_Detection/blob/main/LWF%20model.png"> 
</p>

<p align="center">
  <img width="950" height="400" src="https://raw.githubusercontent.com/sravanikuncham466/DSBA_6165_Forest_Fire_and_Smoke_Detection/main/Fine%20tune%20Xception.png">
</p>

## 📌 Objective

The goal of this project is to build a deep learning model that can detect fire-related phenomena — including new and emerging conditions like haze — **without retraining from scratch**.
 
Specifically, we aim to:
- Develop a classification system for `fire`, `nofire`, `smoke`, `smokefire`, and `haze`
- Preserve performance on previously learned classes when adding new ones
- Implement a **Learning without Forgetting (LwF)** strategy to enable this incremental learning

## ⚙️ Methods Tried

<p align="center">
<img width="900" height="500" src="https://github.com/sravanikuncham466/DSBA_6165_Forest_Fire_and_Smoke_Detection/blob/main/Methodology.png">
</p>

We explored multiple model development strategies to classify five classes: `fire`, `nofire`, `smoke`, `smokefire`, and `haze`.
 
1. **Baseline Models** 
   - **VGG16** and **Xception**, both pretrained on ImageNet 
   - Trained directly on the 5-class dataset 
   - Served as initial benchmarks
 
2. **Fine-Tuned Xception** 
   - Xception model fine-tuned on the original 4 classes (`fire`, `nofire`, `smoke`, `smokefire`) 
   - Last 30 layers unfrozen for domain adaptation 
   - Provided a strong teacher model for LwF
 
3. **Incremental Learning with LwF** 
   - Introduced the `haze` class without retraining on original data 
   - Student model trained with:
 	- **Hard loss**: Categorical cross-entropy on true labels
 	- **Soft loss**: KL-divergence from teacher model predictions (temperature=2.0) 
   - Combined loss: `L_total = α * SoftLoss + (1 - α) * HardLoss` with `α = 0.5`

## 🧠 Conclusion
 
- This project demonstrates how **Learning without Forgetting (LwF)** can enable incremental learning in image classification tasks related to forest fire detection.
 
By extending a fine-tuned Xception model with a new class (`haze`), we successfully trained a student model that:
- Maintains high accuracy on previously learned classes (`fire`, `nofire`, `smoke`, `smokefire`)
- Learns the new class (`haze`) without requiring access to original training data
- Achieves performance comparable to full retraining, with significantly lower computational cost
 
Our results show that LwF is a practical and scalable approach for real-world systems that must continuously evolve without forgetting prior knowledge.
 
## References:
Paper 1: https://www.researchgate.net/publication/367539352_An_Improved_Forest_Fire_Detection_Method_Based_on_the_Detectron2_Model_and_a_Deep_Learning_Approach

Paper 2: 
https://www.sciencedirect.com/science/article/pii/S2405844023103355

Paper 3:
https://www.techscience.com/csse/v44n2/48251/html

Paper 4:
https://fireecology.springeropen.com/articles/10.1186/s42408-022-00165-0


