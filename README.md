# Deep Learning for Canine Cardiomegaly Detection

This repository contains two projects focused on diagnosing **canine cardiomegaly** (enlarged heart) from dog X-ray images using deep learning.

---

## 📌 Project 1: Dog Heart Classification

**Objective**:  
To classify dog X-ray images into three categories — **Cardiomegaly**, **Normal**, or **Others**, using a custom-built **Convolutional Neural Network with a Bidirectional Long Short-Term Memory (CNN-BiLSTM)** model.

### 🧠 Model Architecture: CNN-BiLSTM

The model is a hybrid architecture that combines the spatial feature extraction capabilities of a CNN with the sequential modeling strength of a BiLSTM.

- **CNN Backbone**:  
  A series of convolutional layers with batch normalization and max pooling to extract hierarchical features from the images.

- **BiLSTM Layers**:  
  Two stacked BiLSTM layers to capture contextual information from the extracted feature sequences.

### 📂 Dataset

The model is trained on the [**Dog Heart**](https://github.com/YoushanZhang/Dog-Cardiomegaly) dataset, which is split into:
- **Training set**: 1400 images  
- **Validation set**: 200 images

Data augmentation techniques such as random flips, rotations, and color jittering are applied to improve generalization.

### 🏋️ Training and Results

- Trained for **128 epochs** using the **Adam optimizer** and **Cross-Entropy Loss**.
- Learning rate scheduling via **ReduceLROnPlateau** and **early stopping** to prevent overfitting.

**Final Test Accuracy**: **73.00%**

📄 Read the full report:  
[**Deep Feature Extraction Using BiLSTM for Canine Cardiomegaly Detection**](https://www.researchgate.net/publication/385944098_Deep_Feature_Extraction_Using_BiLSTM_for_Canine_Cardiomegaly_Detection)

---

## 📌 Project 2: Vertebral Heart Size (VHS) Point Detection

**Objective**:  
To detect six key anatomical points in dog X-ray images to calculate the **Vertebral Heart Size (VHS)** — a quantitative measure of cardiac size.

This project uses a **High-Resolution Network (HRNet)** for keypoint regression.

### 🧠 Model Architecture: HRNetKeypointRegressor

This model leverages a pre-trained HRNet, a state-of-the-art architecture for human pose estimation, adapted for this specific veterinary task.

- **Backbone**:  
  A `timm`-based `hrnet_w32` model, pre-trained on ImageNet, is used for robust feature extraction.

- **Regressor**:  
  Fully connected layers are added to regress the `(x, y)` coordinates of the six anatomical keypoints.

### 📂 Dataset

A custom dataset of dog X-ray images is used, annotated with:
- Six keypoint coordinates per image  
- Ground truth VHS values

All images are:
- Resized to **512x512 pixels**
- Keypoint coordinates are **normalized** with respect to image dimensions

### 🏋️ Training and Results

- Trained for **200 epochs** using the **Adam optimizer** and **Mean Squared Error (MSE) loss**

**Final Test Accuracy**: **77.50%**

The model outperforms VGG16 in localizing anatomical keypoints, ensuring reliable VHS computation. The predicted keypoints closely align with the ground truth across validation samples.

<img width="262" height="279" alt="image" src="https://github.com/user-attachments/assets/0934f29f-ef75-41e4-8450-73960c53852c" />


📄 Read the full report:  
[**HRNet-Based Keypoint Localization for Vertebral Heart Score Prediction in Dogs**](https://www.researchgate.net/publication/386424985_HRNet-Based_Keypoint_Localization_for_Vertebral_Heart_Score_Prediction_in_Dogs)
