# **Plant Disease Detection Model - Report**

## **Table of Contents**
- [Week 1: Data Preprocessing & Loading](#week-1-data-preprocessing--loading)
- [Week 2: Model Architecture & Training](#week-2-model-architecture--training)
- [Week 3: Model Evaluation & Optimization](#week-3-model-evaluation--optimization)
- [Week 4: Deployment & Final Testing](#week-4-deployment--final-testing)

## **Week 1: Data Preprocessing & Loading**

### **What I Did**

#### **Data Preprocessing & Loading**
I prepared the dataset using **Keras' ImageDataGenerator**, which helps load and preprocess images efficiently.

##### **Training Data Preparation**
- **Resized images** to 224x224 pixels to ensure uniform input size.
- **Rescaled pixel values** from 0-255 to 0-1 using `rescale=1/255.0` to improve model convergence.
- **Applied data augmentation** (rotation, flipping) to enhance model generalization.
- **Loaded images from directories** and applied **one-hot encoding** to labels (`class_mode='categorical'`).
- **Created batches** of 164 images to optimize memory usage during training.

##### **Validation Data Preparation**
- Used **10% of available data for validation** (`validation_split=0.1`).
- Ensured **no shuffling** (`shuffle=False`) to maintain a consistent dataset structure.
- Found **1,742 images** distributed across 38 classes.

##### **Test Data Preparation**
- Used the **same dataset path as validation** (as no separate test folder was provided).
- Rescaled images similarly (`rescale=1/255.0`).
- Loaded **entire dataset for testing**, resulting in **17,572 images across 38 classes**.

##### **Class Mapping Verification**
I printed `test_generator.class_indices` to verify that class labels were correctly mapped. The output showed a dictionary mapping class names to numerical indices (0-37), ensuring the model's predictions align with disease names.

## **Week 2: Model Architecture & Training**

_(To be updated)_

## **Week 3: Model Evaluation & Optimization**

_(To be updated)_

## **Week 4: Deployment & Final Testing**

_(To be updated)_

---
This markdown file will be continuously updated to document my progress. Let me know if you need any modifications!
