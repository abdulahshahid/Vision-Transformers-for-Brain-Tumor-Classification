
![image](https://github.com/user-attachments/assets/2b81cddf-337d-48c1-a329-6e242ba0136f)

# Vision Transformers for Brain Tumor Classification
### **Introduction**

#### **Overview of the Project**
This project involves the application of Vision Transformers (ViTs) for the classification of MRI images into four distinct categories: glioma tumor, meningioma tumor, no tumor, and pituitary tumor. The project explores both a **custom-built Vision Transformer model** and a pre-trained **EfficientNetB0**, aiming to determine the most effective approach for this classification task within the medical imaging domain.

#### **Objectives of the Project**
The primary objectives of this project are:
- To design and implement a Vision Transformer model from scratch and evaluate its performance on a medical dataset.
- To fine-tune a pre-trained Vision Transformer model and compare its performance against the custom-built model.
- To analyze the effectiveness of Vision Transformers in medical image classification, particularly for brain tumor detection.

#### **Why Vision Transformers?**
Vision Transformers have revolutionized image processing by capturing global dependencies and patterns in images, making them highly effective for tasks requiring precision, such as medical image classification. This project leverages the strengths of ViTs to improve the accuracy and reliability of MRI image classification.

---

### **Dataset**

#### **Description of the Dataset**
The dataset used in this project comprises MRI scans, categorized into four classes:
1. Glioma Tumor
2. Meningioma Tumor
3. No Tumor
4. Pituitary Tumor

The dataset is structured with separate training and testing sets, where each image is resized to 72x72 pixels to be compatible with the Vision Transformer models.

- **Dataset Link**: [Brain Tumor Classification MRI](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri)

#### **Dataset Statistics**
- **Total Images**: 394
- **Training Images**: 274
- **Testing Images**: 120
- **Number of Classes**: 4
- **Class Distribution**:
  - Glioma Tumor: 100 images
  - Meningioma Tumor: 115 images
  - No Tumor: 105 images
  - Pituitary Tumor: 74 images

#### **Data Sources and Accessibility**
The dataset was sourced from Kaggle, a well-known platform for sharing datasets. The specific dataset used for this project is publicly accessible and is particularly suited for research and development in medical imaging.

---

### **Preprocessing**

#### **Data Preparation Steps**
- **Image Resizing**: All images were resized to 72x72 pixels to maintain uniform input dimensions for the Vision Transformer models.
- **Normalization**: Pixel values were normalized to the range [0, 1] to facilitate faster convergence during training.
- **Data Augmentation**: Several augmentation techniques, including rotation, width and height shifts, shear transformation, and zooming, were applied to increase the diversity of the training data.

#### **Data Augmentation Techniques**
- **Rotation Range**: 20 degrees
- **Width Shift Range**: 0.2
- **Height Shift Range**: 0.2
- **Shear Range**: 0.2
- **Zoom Range**: 0.2
- **Horizontal Flip**: Enabled

#### **Handling Class Imbalance**
To handle class imbalance, the Synthetic Minority Over-sampling Technique (SMOTE) was employed. SMOTE generated synthetic samples for the minority classes, ensuring that the model received a balanced representation of each class during training.

---

### **Models**

#### **Vision Transformer (ViT) Built from Scratch**

##### **Model Architecture**
The custom Vision Transformer model was built from scratch, using a patch size of 6x6 and a projection dimension of 64. The model featured 8 transformer layers, each containing multi-head attention mechanisms and multilayer perceptrons (MLP) with hidden units [128, 64]. Positional embeddings were added to the patch embeddings to retain spatial information.

##### **Hyperparameters and Configuration**
- **Learning Rate**: 0.001
- **Batch Size**: 256
- **Epochs**: 100
- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy
##### **Results**
![Model accuracy and loss over epoch](https://github.com/user-attachments/assets/c5be6ec1-1c6d-4fa6-a3da-1e6ecb5634ff)
![Classification Report](https://github.com/user-attachments/assets/1d524ce9-4650-4381-9d20-c4318e95aac0)
![Classification Matrix](https://github.com/user-attachments/assets/b0b404c6-1744-45f0-83cb-bf5231c838d1)

#### **Pre-trained Vision Transformer**

##### **Model Architecture**
A pre-trained model, **EfficientNetB0**, was fine-tuned on the medical dataset. The base model was pre-trained on ImageNet, providing a solid foundation for transfer learning. The top layers were customized to match the number of classes in the medical dataset.

##### **Transfer Learning Strategy**
During the initial training phases, the pre-trained layers were frozen, allowing only the top layers to be trained. Subsequently, the entire model was fine-tuned to further enhance accuracy.

##### **Hyperparameters and Configuration**
- **Learning Rate**: 0.001
- **Batch Size**: 32
- **Epochs**: 50
- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy
##### **Results**
![image](https://github.com/user-attachments/assets/b6f05bf7-b382-4127-a901-cc8647d4cc06)
![image](https://github.com/user-attachments/assets/8620a7d1-469f-4759-bc77-1e3176c291c6)
![image](https://github.com/user-attachments/assets/bf5be845-a5be-4d94-bb68-c8844d78521a)

---
### **Conclusion**

#### **Summary of Findings**
This project demonstrated the effectiveness of Vision Transformers for medical image classification, achieving high accuracy on a challenging dataset. The comparison between a custom-built model and a pre-trained model highlighted the benefits of transfer learning in terms of both performance and training efficiency.

#### **Future Work and Improvements**

Future work could explore the use of larger datasets, different pre-trained models, and the application of Vision Transformers to other medical imaging tasks. Additionally, hyperparameter tuning and model ensemble techniques could further enhance accuracy.

---

This content follows the detailed Table of Contents you provided and is tailored to the work you’ve done on the Vision Transformer project. You can now add any images and finalize the report. Let me know if you need any further assistance!
