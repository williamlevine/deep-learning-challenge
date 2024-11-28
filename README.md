# Deep Learning Challenge - Module 21
# Overview of the Analysis

The goal of this analysis is to build and evaluate a deep learning model to predict whether a charity application will be successful based on various features. The model aims to classify charity applications as either successful or not, using multiple input variables related to the application, such as `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, and others. The process includes data preprocessing, model training, and evaluation to achieve an accuracy greater than 75%.


# Results

## Data Preprocessing

- **Target Variable**:
  - The target variable for the model is `IS_SUCCESSFUL`, as it represents whether a charity application is successful or not.

- **Feature Variables**:
  - The feature variables are:
    - `APPLICATION_TYPE`
    - `AFFILIATION`
    - `CLASSIFICATION`
    - `USE_CASE`
    - `ORGANIZATION`
    - `INCOME_AMT`
    - `SPECIAL_CONSIDERATIONS`
  - These variables contain information that will be used to predict the outcome of the application.

- **Variables to Remove**:
  - The following variables should be removed from the input data as they are not relevant to the features or target:
    - `EIN` (Employer Identification Number)
    - `NAME` (Name of the charity)
  - These are identifiers and do not provide useful information for predicting the success of a charity application.

---

## Compiling, Training, and Evaluating the Model

- **Neurons, Layers, and Activation Functions**:
  - The neural network consists of:
    - **Input Layer**: Number of neurons equal to the number of features in the dataset.
    - **First Hidden Layer**: 80 neurons with `ReLU` activation function.
    - **Second Hidden Layer**: 30 neurons with `ReLU` activation function.
    - **Output Layer**: 1 neuron with `sigmoid` activation function to output a probability between 0 and 1 for classification.
  - **Reason for choices**: `ReLU` is commonly used for hidden layers as it helps avoid the vanishing gradient problem. The `sigmoid` activation is used in the output layer because it's appropriate for binary classification tasks.

![Screenshot (272)](https://github.com/user-attachments/assets/d08fd858-a5bc-4864-b296-6ee05758c670)

- **Model Performance**:
  - The model achieved a final accuracy of **72.78%**.
  - **Target performance (75%)** was not reached, but the model was able to perform decently with the available data.

- **Steps to Improve Model Performance**:
  - Increased number of neuron layers to three.
  - Increased number of units to 128, 64, and 32.
  - Tried `thela` activation function.
  - Decreased epochs from 100 to 50.

Other than the epoch reduction, these steps all resulted in a decrease in accuracy. I thus deleted one of the neuron layers and lowered the number of units back to 80 and 30. The `thela` function also worsened the model's accuracy, so I reverted back to the `ReLU` function. The only thing that helped was reducing the epochs to 50, so the final model uses 50 epochs instead of 100.

![Screenshot (273)](https://github.com/user-attachments/assets/5060f1e0-340d-46d2-9e3e-44728e6d48d4)

---

# Summary

- **Overall Results**:
  - The deep learning model achieved an accuracy of **72.78%**, which was below the desired 75% threshold.
  - Despite attempts to improve the model through various tuning and regularization strategies, the accuracy remained under the target.
  
- **Recommendation for a Different Model:**
  - A **Random Forest** or **Gradient Boosting Machine (GBM)** model could be a great alternative to a deep learning model. These methods work really well for sorting tasks with structured data like this, especially when understanding which factors are most important is key. Unlike deep learning, which needs a lot of data and careful adjustments, tree-based models like Random Forest and GBM are easier to set up and often perform just as well without the risk of overfitting.

- **Conclusion**:
  - Although a deep learning model showed promise, alternative machine learning models such as **Random Forest** or **Gradient Boosting** might be more effective for this classification problem and easier to optimize.
