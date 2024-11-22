


# STEELFACTORY

## ArshamPredictions - Main Code 

**Project for Applied Machine and Deep Learning**  
**Author: Arsham Moayedi Far**

---

### 1. Importing Libraries 
To start, all necessary libraries for the project are imported.

### 2. Reading the Dataset
The training and testing datasets are merged and loaded for use in subsequent steps.  
This section also includes a brief analysis to understand the dataset's nature.

### 3. EDA (Exploratory Data Analysis)
In this section, the following data-cleaning steps are performed:
- Removing NaN values
- Handling outliers

### 4. Feature Importance (FI) Analysis
Feature importance is analyzed to understand each input parameter's effect on the output.  
The following approaches are used for Feature Importance:
- **Correlation Matrix**
- **DecisionTreeRegressor**
- **RandomForestRegressor**
- **XGBRegressor**

![FI_CM](https://github.com/user-attachments/assets/0e3056d8-00e9-42e7-a581-6740c16a4296)

FI using Correlation Matrix



![FI_DT](https://github.com/user-attachments/assets/ab160427-bdf5-4119-967f-ab385d450d83)

FI using DecisionTreeRegressor


![FI_RF](https://github.com/user-attachments/assets/023abc92-b552-4a34-8ec1-0c92f2bf3072)

FI using RandomForestRegressor


![FI_XGB](https://github.com/user-attachments/assets/54d0fe8c-3f80-483c-bc30-811088d6b5d7)

FI using XGBRegressor

### 5. Visualization
The following visualizations are used to understand parameter distributions:

- **Histogram Plots**
- **Violin Plots**



![histplot](https://github.com/user-attachments/assets/9807718a-35f1-4255-bea6-293e7c3b7feb)

Histogram plots 


![violinplot](https://github.com/user-attachments/assets/88f63146-5c0c-4c10-843e-d39e976e08b5)

Violin plots



### 6. Deleting unnecessary features and Splitting Dataset (train-validation-test)
The following visualizations are used to understand parameter distributions:

Based on FI results, the following features are removed from further evaluation: 7, 15, and 18.

The dataset is then split into training, validation, and test sets using the following code:


###### First split into training and temporary sets (80% train, 20% temp)
x_train, x_temp, y_train, y_temp = train_test_split(X, Y, test_size=0.20, random_state=0)

###### Now split the temporary set into validation and test sets (50% of temp, so 10% of the total each)
x_val, x_test, y_val, y_test = train_test_split(x_temp, y_temp, test_size=0.50, random_state=0)



### 7. Training Models



1) For this step various types of ML algorithms consisting of: SVR, RF, XGB and DT
2) For each of them,  cross_validation, Hyperparameter tuning, Plots and evaluation index were derived and investigated.
2-1) As I did not have access to a capable PC to do the training in a reasonable time frame, I should have decreased the allowable range of variables in the hyperparameter section. However, it has been employed to show my knowledge in ML for the project.
3) Moreover, different indexes were considered to show their performance. However, due to the sensitivity of MAPE to scaling (MAPE is generally sensitive to the scale of the data, as it’s designed to work with absolute percentage differences relative to the original values. When data is standardized, the absolute percentage loses meaning, making MAPE a less suitable metric.) it was not considered.

![Train_ModelI_SVR](https://github.com/user-attachments/assets/42f61621-2ac4-4fb4-bc36-7f8d8b4e44ed)

Results for SVR Train set

![Val_ModelI_SVR](https://github.com/user-attachments/assets/424933db-17a8-428c-a12b-cb97ef60c7d9)

Results for SVR Validation set

![Train_ModelI_XGB](https://github.com/user-attachments/assets/49304925-bdfe-4c55-96a5-ed106b76a6c3)

Results for XGB Train set

![Val_ModelI_XGB](https://github.com/user-attachments/assets/73c2eae1-2fd3-4773-824e-8c7e72e898bb)

Results for XGB Validation set

![Train_ModelI_RF](https://github.com/user-attachments/assets/080724fa-5a69-45da-b659-46f54b03447d)

Results for RF Train set

![Val_ModelI_RF](https://github.com/user-attachments/assets/19435183-9af4-4e2e-825f-79f9af672feb)

Results for RF Validation set

![Train_ModelI_DT](https://github.com/user-attachments/assets/ea55207d-e1b1-4b60-b670-52c9b4f49176)

Results for DT Train set

![Val_ModelI_DT](https://github.com/user-attachments/assets/dd3941c5-375b-4fd6-95de-7d360dda842b)

Results for DT Validation set


As it is shown, DT's Prediction suffers from over-fitting.


# 8- Predictions based on Test dataset

In this part the seperated test dataset is considered for checking and analyasing the final performance of the trained algorithms:

![regression_metrics_table](https://github.com/user-attachments/assets/f5610cf8-3bc7-4e2f-a7a5-d7d8dfc63dcd)
Performance of the trainde models based on Test dataset.
As it is shown RF possesses the best results with R2 = 0.515 and RMSE= 0.063 followed by XGB with R2= 0.481 and RMSE= 0.065.
As it was mentioned perviously, DT has the worst performance among the considered cases.
It should also be mentioned that due to the lack of computational capability the considered range of hyperparameter tuning is limited which had negatively influenced the results.


# 9- Saving the algorithms

In the last part, trained modeles were save for furthur usage of other users employing the "joblib"
