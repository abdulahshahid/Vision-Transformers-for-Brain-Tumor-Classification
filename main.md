# Intrusion Detection System (IDS) for Network Traffic Analysis

## Overview
This project is centered around enhancing network security by developing a robust Intrusion Detection System (IDS) that utilizes machine learning and deep learning methodologies. By tapping into the comprehensive CICIDS2017 dataset, we aim to craft models that can accurately identify various network threats in contrast to normal traffic. Our ultimate goal is to boost the precision and responsiveness of network defenses through an interactive interface designed for real-time attack detection.

## Objectives
- **Explore and Analyze the CICIDS2017 Dataset:** We explore the dataset to understand the dynamics and distribution of network attacks.
- **Data Preprocessing:** We implement key preprocessing steps like handling missing data, encoding categorical variables, and normalizing features, setting the stage for effective modeling.
- **Feature Selection:** Using statistical techniques such as the Chi-squared test, we pinpoint critical features that significantly impact our models' predictive power.
- **Model Training and Evaluation:** We develop and rigorously evaluate a Random Forest Classifier and a Deep Neural Network (DNN) to ensure they meet high standards of accuracy and reliability.
- **Address Class Imbalance:** We apply the Synthetic Minority Over-sampling Technique (SMOTE) to ensure our models perform well across diverse attack types.
- **Real-Time Detection Interface:** We are also developing an interactive interface that integrates our trained models, facilitating real-time detection and classification of network threats.
- **Model Deployment:** The models are prepared for deployment, enabling seamless integration into existing network security frameworks to enhance real-time threat detection capabilities.


---

# Dataset

The project utilizes the CICIDS2017 dataset, sourced from the Canadian Institute for Cybersecurity. This comprehensive dataset includes benign traffic and 14 types of simulated network attacks and one BENIGN class, categorized as follows:

- **General Attacks**: DDoS, PortScan
- **DoS Variants**: DoS GoldenEye, DoS Hulk, DoS Slowhttptest, DoS slowloris
- **Web Attacks**: Web Attack - Brute Force, Web Attack - SQL Injection, Web Attack - XSS
- **Other Attacks**: Heartbleed, Infiltration, Bot

Each CSV file within the dataset represents different network behaviors, enabling detailed training of the IDS to effectively identify and differentiate between these varied attack types alongside benign traffic.


---

# Exploratory Data Analysis (EDA)

During the exploratory data analysis phase, several key insights were gathered, supported by the following visualizations:

1. **Frequency of Each Type of Network Attack**:  
   ![image](https://github.com/user-attachments/assets/fba17750-b508-4306-b188-75cb7d7481b3)


2. **Window Size Analysis Across Different Attacks**:  
   ![image](https://github.com/user-attachments/assets/635092bf-0c7e-4a7b-b50e-3e9dc552417c)


3. **Active vs. Idle Times in DDoS Attacks**:  
   ![image](https://github.com/user-attachments/assets/26dacd82-16a0-4017-ae74-69a7985fd65a)
---

## Preprocessing

In preparing the dataset for model training, several key preprocessing steps were undertaken:

1. **Removing Null and Infinite Values**:  
   - We removed any rows with null or infinite values to ensure data quality.

2. **Encoding Categorical Features**:  
   - Categorical features were converted into numerical values using `LabelEncoder` from `sklearn`.

3. **Handling Class Imbalance with SMOTE**:  
   - We addressed class imbalance using the Synthetic Minority Over-sampling Technique (SMOTE). Below is a table showing the class distribution before and after resampling:

| Class Label | Original Count | Resampled Count |
|-------------|----------------|-----------------|
| 0           | 439,683        | 439,683         |
| 1           | 1,956          | 439,683         |
| 2           | 128,025        | 439,683         |
| 3           | 10,293         | 439,683         |
| 4           | 230,124        | 439,683         |
| 5           | 5,499          | 439,683         |
| 6           | 5,796          | 439,683         |
| 7           | 7,935          | 439,683         |
| 8           | 11             | 439,683         |
| 9           | 36             | 439,683         |
| 10          | 158,804        | 439,683         |
| 11          | 5,897          | 439,683         |
| 12          | 1,507          | 439,683         |
| 13          | 21             | 439,683         |
| 14          | 652            | 439,683         |

4. **Feature Selection using Chi-Square**:  
   - We selected the 20 most significant features using the Chi-square test:
   - **Selected Features**: 'Flow Duration', 'Total Length of Fwd Packets', 'Fwd Packet Length Max', 'Flow Bytes/s', 'Flow Packets/s', 'Flow IAT Mean', 'Flow IAT Std', 'Flow IAT Max', 'Fwd IAT Total', 'Fwd IAT Mean', 'Fwd IAT Std', 'Fwd IAT Max', 'Fwd IAT Min', 'Bwd Packets/s', 'Packet Length Mean', 'Packet Length Std', 'Packet Length Variance', 'Average Packet Size', 'Subflow Fwd Bytes', 'Active Min'

5. **Feature Scaling**:  
   - Features were standardized using `StandardScaler` from `sklearn` to ensure uniform contribution to the model.


---

## Model Training

After preprocessing, the dataset was ready for model training. We implemented two machine learning models and one deep learning model to classify the network attacks:

### 1. **Random Forest Classifier**  
   - **Model Selection**: We chose a Random Forest Classifier for its robustness and ability to handle large datasets effectively.
   - **Training**: The model was trained using the resampled dataset, with 20% of the data reserved for testing. 
   - **Performance**: The Random Forest model achieved a high accuracy, and its performance was evaluated using various metrics such as the classification report, confusion matrix.

   **Key Metrics**:
   - **Accuracy**: Provided insight into the overall performance of the model.
![image](https://github.com/user-attachments/assets/b7428a9e-c873-4908-a60d-28d1ab991d1c)

   - **Confusion Matrix**: Visualized the model's ability to correctly classify the different attack types.
![image](https://github.com/user-attachments/assets/0a59618a-d289-4041-ad7f-978da4c37761)
   
### 2. **Deep Neural Network (DNN)**  
   - **Model Architecture**: The DNN model consisted of an input layer, two hidden layers with dropout for regularization, and an output layer using softmax activation to handle multi-class classification.
   - **Training**: The DNN was trained over 20 epochs with a batch size of 32, using the categorical cross-entropy loss function.
   - **Performance**: The DNN model’s performance was evaluated using similar metrics as the Random Forest, including accuracy, classification report, and confusion matrix.

   **Key Metrics**:
   - **Accuracy**: Evaluated how well the DNN model classified the network attacks.
![image](https://github.com/user-attachments/assets/c7c307b9-f698-47fb-8c59-8a550daadee7)
   - **Confusion Matrix**: Provided detailed insights into the performance of the DNN model across all attack types.
![image](https://github.com/user-attachments/assets/4d6ee1b4-fab8-476e-8987-1bd16a938b07)

   **Model Saving**:
   - The DNN model was saved in the HDF5 format (`.h5`) using TensorFlow’s `save` method.

### 3. **Model Selection for Inference**
   - The trained models (Random Forest and DNN) were integrated into a Streamlit interface for real-time attack detection, where users can input network parameters and receive a classification prediction.

---
