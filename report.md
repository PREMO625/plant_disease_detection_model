# **Plant Disease Detection Model - Report**
## **Week-1**

### **1.1 Data Preprocessing & Loading**
I prepared the dataset using **Keras' ImageDataGenerator**, which helps load and preprocess images efficiently.

#### **Training Data Preparation**
- **Resized images** to 224x224 pixels to ensure uniform input size.
- **Rescaled pixel values** from 0-255 to 0-1 using `rescale=1/255.0` to improve model convergence.
- **Applied data augmentation** (rotation, flipping) to enhance model generalization.
- **Loaded images from directories** and applied **one-hot encoding** to labels (`class_mode='categorical'`).
- **Created batches** of 164 images to optimize memory usage during training.

#### **Validation Data Preparation**
- Used **10% of available data for validation** (`validation_split=0.1`).
- Ensured **no shuffling** (`shuffle=False`) to maintain a consistent dataset structure.
- Found **1,742 images** distributed across 38 classes.

#### **Test Data Preparation**
- Used the **same dataset path as validation** (as no separate test folder was provided).
- Rescaled images similarly (`rescale=1/255.0`).
- Loaded **entire dataset for testing**, resulting in **17,572 images across 38 classes**.

#### **Class Mapping Verification**
I printed `test_generator.class_indices` to verify that class labels were correctly mapped. The output showed a dictionary mapping class names to numerical indices (0-37), ensuring the model's predictions align with disease names.

## **3. What I Learned**
Through this process, I gained the following insights:

1. **Understanding Data Augmentation**:  
   - Augmentation helps create variations in images to improve model robustness.
   - Even though this dataset was pre-augmented, additional augmentation can still be applied dynamically during training.

2. **Why Rescaling is Important**:
   - Rescaling (dividing pixel values by 255) ensures images have values between 0-1, making model training more stable and efficient.

3. **What One-Hot Encoding Does**:
   - Instead of assigning labels as numbers (e.g., Apple Scab = 0, Black Rot = 1), one-hot encoding represents them as vectors (e.g., `[1, 0, 0, 0]` for class 0).
   - This prevents the model from assuming numerical relationships between categories.

4. **How `flow_from_directory()` Works**:
   - It loads images **directly from folders** instead of needing a CSV file.
   - It automatically **assigns class labels** based on folder names.
   - It enables **batch processing** to handle large datasets efficiently.

5. **Difference Between Validation and Test Data**:
   - **Validation Set** is used during training to monitor model performance.
   - **Test Set** is used only after training to evaluate final accuracy.

6. **Importance of Checking Class Indices**:
   - Ensuring that disease names map correctly to class indices prevents label mismatches, which could lead to incorrect predictions.

## **4. Next Steps**
Now that the dataset is loaded and preprocessed, the next step is **building and training a Convolutional Neural Network (CNN)** to classify plant diseases accurately.


