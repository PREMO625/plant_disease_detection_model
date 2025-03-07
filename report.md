# **Plant Disease Detection Model - Report**

## **Table of Contents**
- [Week 1: Data Preprocessing & Loading](#week-1-data-preprocessing--loading)

---

## **Week 1: Data Preprocessing & Loading**

### **1.1 Data Preprocessing & Loading**

**Training Data Preparation:**
- **Resized Images:** All images were resized to 224x224 pixels to ensure uniform input size.
- **Rescaled Pixel Values:** Pixel values were normalized from 0–255 to 0–1 using `rescale=1/255.0` to improve model convergence.
- **Data Augmentation:** Applied rotation and flipping to enhance model generalization.
- **Directory-Based Loading:** Used `flow_from_directory()` to load images directly from folders with one-hot encoding (`class_mode='categorical'`).
- **Batch Processing:** Created batches of 164 images to optimize memory usage during training.

**Validation Data Preparation:**
- **Validation Split:** Used 10% of the available data (`validation_split=0.1`) for validation.
- **No Shuffling:** Set `shuffle=False` to maintain a consistent dataset structure.
- **Dataset Size:** Found 1,742 images distributed across 38 classes.

**Test Data Preparation:**
- **Using Validation Path:** Employed the same dataset path as validation (no separate test folder provided).
- **Consistent Preprocessing:** Rescaled images similarly (`rescale=1/255.0`).
- **Dataset Size:** Loaded the entire dataset for testing, resulting in 17,572 images across 38 classes.

**Class Mapping Verification:**
- Printed `test_generator.class_indices` to verify correct mapping of class names to numerical indices (0-37), ensuring the model's predictions align with the intended disease names.

---

### **1.2 Improvements Implemented in Week 1**

**Exploratory Data Analysis (EDA):**
- **Class Distribution:** Verified using bar plots to check for class imbalance.
- **Data Integrity:** Checked for corrupt or missing images and confirmed that there were 0 corrupt images.
- **Quality Verification:** Visualized sample images from each class to ensure overall dataset quality.

**Data Preprocessing Enhancements:**
- **Basic Preprocessing:** Resized images to 224x224 pixels and normalized pixel values to a 0–1 range.
- **Initial Augmentation:** Applied rotation and flipping.
- **Advanced Augmentation (Optional):** Discussed adding width/height shifts, shear, zoom, and brightness adjustments for further improved generalization.

**Data Loading Optimizations:**
- **Method Comparison:**  
  - Utilized `flow_from_directory()` for on-demand image loading (faster initial output).
  - Explored the `tf.data` API (via `image_dataset_from_directory()`) for potentially faster training through parallel loading, despite a slightly longer initialization time.
- **Note:** The `workers` argument is not supported in `flow_from_directory()`.

**Interactive Image Verification:**
- **Manual Review Script:** Developed a script to manually review and label images as correct or misclassified.
- **Approach Iterations:**  
  - Initially attempted using Matplotlib (faced blocking issues).
  - Tried OpenCV’s `cv2_imshow()` with the Colab patch (disabled in Colab).
  - Ultimately implemented an interactive solution using ipywidgets to display 10 images (labeled A–J) and gather user input on misclassifications.

---

### **1.3 What I Learned**

From the work and improvements implemented in Week 1, I gained valuable insights:

- **Data Augmentation:**  
  Augmentation creates variations in the dataset that help the model generalize better.  
  I learned that even with pre-augmented data, additional dynamic augmentations (like rotation and flipping) are crucial.

- **Image Rescaling:**  
  Normalizing pixel values to a 0–1 range is vital for model stability and efficient convergence during training.

- **One-Hot Encoding:**  
  Converting class labels to one-hot encoded vectors prevents the model from misinterpreting numerical labels as ordinal relationships.

- **Efficient Data Loading:**  
  Loading images directly from directories via `flow_from_directory()` is straightforward, and exploring the `tf.data` API offers potential for improved training performance despite longer initialization times.

- **Verification Processes:**  
  Conducting EDA—such as checking class distribution and ensuring data integrity—ensures that the dataset is balanced and of high quality, which is essential for building robust models.

- **Interactive Verification Tools:**  
  Using interactive methods (ipywidgets) for manual image review helps in cleaning the dataset and ensuring correct labeling before moving to model training.

---

### **1.4 Next Steps**

- With the dataset successfully loaded and preprocessed, the next phase is to **build and train a Convolutional Neural Network (CNN)** to classify plant diseases.


---

## Week 2 Report

### What Was Done
- **Model Architecture & Implementation:**  
  - Developed a Convolutional Neural Network (CNN) using TensorFlow/Keras with multiple convolutional layers, pooling layers, flattening, and dense layers.  
  - The CNN was designed to process 224×224 RGB images and output probabilities for 38 classes corresponding to various plant diseases.
  
- **Training and Evaluation:**  
  - Compiled the model using the categorical crossentropy loss function, Adam optimizer, and monitored metrics such as accuracy, precision, and recall.
  - Utilized data generators with augmentation to feed the training and validation data into the model.
  - Employed callbacks like EarlyStopping, ModelCheckpoint, and ReduceLROnPlateau to optimize the training process and prevent overfitting.
  - Trained the model for 5 epochs, achieving training accuracy of around 98% and validation accuracy close to 91%.
  - Evaluated the model on a separate test set, recording metrics that confirmed the model’s promising performance.

- **Model Saving:**  
  - Saved the complete trained model to disk (`cnn_model.keras`), which includes the architecture, weights, and optimizer state for future use.

### What I Learned
- **Deep Learning Fundamentals:**  
  - Gained hands-on experience in designing and training CNNs for image classification.
  - Understood how convolutional layers extract hierarchical features (edges, textures, patterns) essential for recognizing plant diseases.

- **Data Augmentation & Preprocessing:**  
  - Learned the importance of augmenting data to improve model generalization and robustness, especially in the context of varied image conditions in agriculture.
  - Improved skills in using data generators and image preprocessing pipelines.

- **Model Optimization Techniques:**  
  - Implemented and observed the impact of callbacks such as EarlyStopping, ModelCheckpoint, and ReduceLROnPlateau, which helped in fine-tuning the learning process.
  - Analyzed training and validation metrics to detect potential overfitting and performance plateaus.

- **Model Persistence:**  
  - Understood the significance of saving the complete model for later deployment, ensuring reproducibility and ease of integration into production systems.

### Next Steps (Deployment Focus)
- **Interactive Deployment:**  
  - Plan to deploy the model through an interactive web application using Streamlit.
