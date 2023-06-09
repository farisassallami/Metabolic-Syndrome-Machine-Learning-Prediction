# Metabolic-Syndrome
- *Author: Faris Assallami*

#  Business Problem

How can we leverage Data Visualizations and Machine Learning techniques to develop a diagnostic model that assists medical professionals in identifying patients with metabolic syndrome, leading to earlier intervention and improved patient outcomes?

## Source of data 
- The dataset for analysis came from the NHANES initiative

## Brief description of data 
- The following description of the data is divided into features of body vitals measurements abnormal waist circumference, triglycerides above 150, HDL cholesterol below 50 in women or 40 in men, history of hypertension and mildly elevated fasting blood sugar (100-125). Numerous other variables were added, such as uric acid, race, income, etc. that might contribute to the model but we will not sure, until we test the model.

-The target is Metabolic Syndrome

-One row represents a patient

-This is a classification problem

-There are 15 features

-There are 2401 rows

#  Loading Data

Loaded the csv file into Jupyter Notebook

# Data Cleaning

Removed irrelevant columns that dont add any insight to the data.  Removed duplicate rows.  Filled in missing data with most frequent value.  Corrected inconsistencies and spelling errors in the data.

# Exploratory Visuals

## Using Histogram Subplots to display numeric features.

![metabolic syndrome numerics](https://user-images.githubusercontent.com/111199631/230153617-f42044a3-1cd9-45d3-9199-63bd27db8854.png)

---------------------------------------------

## Using Countplot to display Metabolic Syndrome by race.

![metabol by race](https://user-images.githubusercontent.com/111199631/230154006-a9346006-e3c1-4713-b260-9c30e8260680.png)

We can see from the count plot above that the proportion of Metabolic Syndrome positivity to negativity higher among the Mexican American and Hispanic communities and the lowest among the Asian communities.

----------------------------------------------

## Using Scatterplot to display the relationship of BMI vs Waist Circumference and Metabolic Syndrome.

![bmi vs waist metabol scatterplot](https://user-images.githubusercontent.com/111199631/230154656-35a84984-eb1f-4d2e-98f7-dbc62f516760.png)

We can see from the scatter plot above that there is a positive relationship between patients who have metabolyc Syndrome and high BMI and Waist circumference.

----------------------------------------------

## Using Scatterplot to display the relationship of BoodGlucose vs Triglyceride-HDL ratio and Metabolic Syndrome.

![bmi triglycericde hdl ratio scatter](https://user-images.githubusercontent.com/111199631/230155309-6b58f343-3259-48e5-b0f6-11402d797f19.png)

We can see from the scatter plot above that there is a positive relationship between patients who have metabolyc syndrome and high bloodglucose tended to have heart conditions by having higher Triglyceride-HDL ratios. Idealy a ratio of 2 or lower is healthy.

----------------------------------------------

## Machine learning

After training the processed data I ran two models.  After tuning both models with optimal parameters the classification reports are below for both models that had the best accuracy and their confusion matrix.

--Tuned Random Forest Model--

Train Classification Report 

              precision    recall  f1-score   support

           0       1.00      1.00      1.00      1182
           1       1.00      1.00      1.00       618

    accuracy                           1.00      1800
   

Test Classification Report 

              precision    recall  f1-score   support

           0       0.88      0.91      0.89       397
           1       0.81      0.76      0.79       204

    accuracy                           0.86       601
   
   

![rftunems](https://user-images.githubusercontent.com/111199631/231800576-af6a93e1-a144-4a5b-9eed-a58f49ffa784.png)







--Tuned KNN Model--

Train Classification Report 

              precision    recall  f1-score   support

           0       0.85      0.92      0.89      1182
           1       0.83      0.69      0.75       618

    accuracy                           0.84      1800
   

Test Classification Report 

              precision    recall  f1-score   support

           0       0.78      0.87      0.82       397
           1       0.68      0.53      0.60       204

    accuracy                           0.76       601
   
   

![knntunems](https://user-images.githubusercontent.com/111199631/231801172-89edbb74-b3f2-4417-be1c-58eac9aa6ee7.png)




After running a GridSearchCV to opbtain opitmal parameters for the KNN model, the accuracy remained the same at 76%.

-------------------------------------------------------

## Model Selection

While the tuned KNN model had the same accuracy than the UN-Tuned KNN model at 76%, overall; the Tuned Random forest model had the highest accuracy of 86% and the Tuned Random Forest model had lowest type 1 & 2 errors than all other models.  For diagnosing metabolic syndrome, its best to have the lowest type 2 error where you minimize the mistake of telling a patient they are healthy while they are actually ill.  Therefore I chose the Tuned Random Forest model.

--------------------------------------------------------

## Recommendations

Based on the 2 scatterplots from earlier above, we can correlate elevated waist circumference, BMI, tryglyceride-hdl ratio, and glucose levels to a patience having metabolic syndrome.  All these features are an indicator of obesity.  Below are 2 recommendations that are highly effective that medical professionals can consult with their patients.

*   Weight loss
*   Diet and lifestyle changes
