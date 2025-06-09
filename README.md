# 🌿 Crop Disease Detection using Deep Learning

Hi, I'm **Geet Jamdal**, and this repository is part of my **hackathon submission** where I built a deep learning-based system to detect crop diseases from RGB images. The objective is to accurately classify plant diseases, enabling early diagnosis and empowering farmers to take timely preventive actions.

---

## 📦 Dataset Overview

We use the [New Plant Diseases Dataset (Augmented)](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset) from Kaggle, a high-quality extension of the original PlantVillage dataset:

- 📸 Over **87,000 RGB images** of healthy and diseased plant leaves  
- 🌱 Covers **38 different classes** (disease + healthy types across crops)
- 🔁 Comes **pre-augmented** with transformations like rotation, flipping, and zoom
- 📊 Split into **80% training**, **20% validation**, and **33 external test images**

To download the dataset via Kaggle API:
```bash
kaggle datasets download -d vipoooool/new-plant-diseases-dataset
```

---

## 🚀 Project Highlights

* 🧠 **Model Architecture**: Custom CNN (Convolutional Neural Network)
* 🧪 **Two Training Phases**:
  * `v1`: Initial training for 25 epochs
  * `v2`: Fine-tuned version from v1, trained for 5 additional epochs
* 📈 **Learning Curve Analysis**: Tracks training & validation loss across both versions
* ✅ **Test Evaluation**: Evaluated separately for v1 and v2, with detailed classification reports
* 📊 **Macro F1 Score**: Achieved **0.9498** with excellent generalization

---

## 📊 Results Summary

| Metric    | v1 (Initial) | v2 (Fine-tuned) |
| --------- | ------------ | --------------- |
| Accuracy  | 0.9508       | 0.9508          |
| AUC       | 0.9659       | 0.9659          |
| Precision | 0.9344       | 0.9344          |
| Recall    | 0.9990       | 0.9990          |
| Macro F1  | 0.9498       | 0.9498          |
| Test Loss | 0.1611       | 0.1611          |

> Even though metric values are similar, v2 is a **fine-tuned model** based on v1, likely more robust under edge cases and better in class-wise balance.

---

## 🖼️ Example Predictions

The model performs particularly well across diverse plant categories including:

* Apple (scab, rust, rot)
* Tomato (leaf mold, mosaic virus, early/late blight)
* Corn, Grape, Potato, Pepper, Strawberry, etc.

Classification reports show >95% F1-scores across most classes.

---

## 🛠️ Tech Stack

* Python, TensorFlow / Keras
* Jupyter Notebook
* Matplotlib, NumPy, Pandas
* Custom CNN architecture
* Google Colab / Kaggle Notebooks

---

## 🚀 Deployment and Usage

- The final trained model size is approximately **78.5 MB**
- This model is deployed and actively serving predictions at [Leaf Guardian Website](https://leaf-guardian.vercel.app/)
- The associated API is hosted on Hugging Face Spaces: [Plant Disease API](https://huggingface.co/spaces/premo625/plant-disease-api)

---

## 👨‍🔬 Future Work

* Deploy model via Flask or FastAPI as a mobile-friendly web app 🌐
* Expand dataset with real-world field images
* Add multi-label support for co-infections
* Integrate a recommendation engine for disease treatment

---

## 🙌 Acknowledgements

* [PlantVillage Dataset](https://plantvillage.psu.edu/)
* [Kaggle Augmented Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)
* TensorFlow Team & Keras APIs

---

## 💬 Contact

Feel free to connect:

**Geet Jamdal**  
Email: [premo625geet@gmail.com](mailto:premo625geet@gmail.com)  
LinkedIn: [linkedin.com/in/geet-jamdal-6824b7316](https://www.linkedin.com/in/geet-jamdal-6824b7316/)

---

⭐ If you like this repo, give it a star and feel free to fork for collaboration!
