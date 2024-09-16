# Cirrhosis Disease Stage Prediction Using Artificial Neural Network

This project analyses clinical trial data from the Mayo Clinic's study on Primary Biliary Cirrhosis (PBC) to predict the histologic stage of the disease using an Artificial Neural Network (ANN). By identifying key features that influence disease progression, the model aims to assist in clinical decision-making and improve patient outcomes.

## **Introduction**

Primary Biliary Cirrhosis is a chronic autoimmune liver disease that can lead to liver failure. Early detection and accurate staging are crucial for effective treatment. This project utilizes machine learning techniques to predict the disease stage based on clinical and laboratory data.

## **Dataset**

The dataset contains clinical trial data collected between 1974 and 1984\. It includes various patient attributes and laboratory measurements. Below is an overview of the variables:

* **Case Number**: Patient identification number.  
* **Time**: Days between registration and the earlier of death, transplantation, or study analysis time.  
* **Status**:  
  * `0`: Censored.  
  * `1`: Censored due to liver transplantation.  
  * `2`: Death.  
* **Drug**:  
  * `1`: D-penicillamine.  
  * `2`: Placebo.  
* **Age**: Age in days.  
* **Sex**:  
  * `0`: Male.  
  * `1`: Female.  
* **Ascites**:  
  * `0`: No.  
  * `1`: Yes.  
* **Hepatomegaly**:  
  * `0`: No.  
  * `1`: Yes.  
* **Spiders** (spider angiomata):  
  * `0`: No.  
  * `1`: Yes.  
* **Edema**:  
  * `0`: No edema and no diuretic therapy.  
  * `0.5`: Edema present without diuretics or resolved with diuretics.  
  * `1`: Edema despite diuretic therapy.  
* **Bilirubin**: Serum bilirubin (mg/dL).  
* **Cholesterol**: Serum cholesterol (mg/dL).  
* **Albumin**: Serum albumin (g/dL).  
* **Copper**: Urine copper (μg/day).  
* **Alkaline Phosphatase**: Enzyme level (U/L).  
* **SGOT**: Serum glutamic-oxaloacetic transaminase (U/mL).  
* **Triglycerides**: Triglycerides (mg/dL).  
* **Platelets**: Platelet count per mm³ / 1000\.  
* **Prothrombin Time**: Seconds.  
* **Stage**: Histologic stage of the disease (1 to 4).

## **Data Preprocessing**

1. **Handling Missing Values**: Missing values are filled with the mean of their respective columns.  
2. **Feature Transformation**:  
   * **Age**: Converted from days to years by dividing by 360\.

## **Exploratory Data Analysis**

A brief EDA was conducted and different types of visualisations such as Histograms, Scatter Plots, Box Plots and Correlation Heatmap were generated. 

### **Key Insights**

* Patients who died had higher bilirubin levels and lower albumin levels.  
* Advanced disease stages are associated with worse patient outcomes.  
* Certain features like bilirubin, albumin, and cholesterol significantly differ across patient statuses.

## **Feature Importance Analysis**

A Decision Tree Classifier is used to identify the most significant features influencing:

1. **Status**: The outcome status of patients.  
2. **Stage**: The histologic stage of the disease.

### **Methodology**

* Split the data into training and testing sets.  
* Scale the features using `StandardScaler`.  
* Fit the Decision Tree Classifier.  
* Plot feature importances to visualise the impact of each feature.

## **Artificial Neural Network Model**

An ANN is implemented from scratch using NumPy to predict the disease stage.

### **Model Architecture**

* **Input Layer**: Selected features based on importance analysis.  
* **Hidden Layers**:  
  * First Hidden Layer: 64 neurons with ReLU activation.  
  * Second Hidden Layer: 32 neurons with ReLU activation.  
* **Output Layer**: Softmax activation for multi-class classification (4 stages).

### **Training Parameters**

* **Learning Rate (`eta`)**: `1e-3`  
* **Epochs**: `10,000`  
* **Loss Function**: Cross-entropy loss  
* **Optimizer**: Gradient Descent

### **Training Procedure**

* Initialise weights and biases randomly.  
* Use forward propagation to compute predictions.  
* Compute loss and perform backpropagation to update weights.  
* Repeat for the specified number of epochs.  
* Plot the training loss curve to monitor convergence.

## **Usage**

### **Preparing the Dataset**

1. Place the `Cirrhosis.csv` file in your working directory.  
2. Update the file path in the script if necessary.

### **Running the Script**

Execute the script in a Python environment or Jupyter Notebook. Ensure all required libraries are installed.

### **Predicting the Disease Stage**

After training, the script allows you to input patient data to predict the disease stage:

1. **User Input**: The script prompts for the following features:  
   * Bilirubin  
   * Albumin  
   * Age  
   * Prothrombin Time  
   * Cholesterol  
   * SGOT  
   * Platelets  
   * Hepatomegaly  
2. **Prediction**: The model outputs the predicted stage of the disease (1 to 4).

## **Results**

* Training Accuracy: The model achieves an overall training accuracy of approximately 0.85 (85%).  
* Loss Curve: The loss decreases over epochs, indicating successful learning.

**Disclaimer: This project is for educational purposes. Clinical decisions should not be based solely on machine learning models without professional medical consultation.**

