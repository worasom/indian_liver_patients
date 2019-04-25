# Indian Liver Patients Data
Automatic liver patients identification from their blood test data. This is a kaggle[https://www.kaggle.com/uciml/indian-liver-patient-records/home] competition. The data is from Lichman, M. (2013). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.

Compare performance of [random forest](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients_random_forest.ipynb), [logistic regression](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_logistic.ipynb), [KNN](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients-KNN.ipynb) and [neural network](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients-NN.ipynb) on identifying liver patients from their blood panel. The traing procedures for each model can be found in the hyperlink.  

There are a number of machine learning papers that work on this data set;for example:
- Bendi Venkata Ramana, Prof. M. S. Prasad Babu and Prof. N. B. Venkateswarlu, "A Critical Comparative Study of Liver Patients from USA and INDIA: An Exploratory Analysis", International Journal of Computer Science Issues, (May 2012)
- Bendi Venkata Ramana and Prof. M.Surendra Prasad Babu, "Liver Classification Using Modified Rotation Forest" International Journal of Engineering Research and Development,  (June 2012)

Analysis Procedures:

- Exploratory data analysis and feature engineering using Python (pandas, numpy, matplot. pyplotlib).
- Experimented with different models (Logistic regression,  random forest classifier, K-nearest neighbors, neural network) using Python (scikit-learn, pytorch, fastai)
- Hyper parameter tuning with randomsearchCV (scikit-learn)
- Calculate feature of importance
- Achieve 78% accuracy on the validation set(baseline = 72%) , loss =  0.47(baseline 0.69) 

# Exporatory Data Analysis 

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig1.png)

Observations:

The gender column is a string. We have to encode the Gender columns. I will encode on a copy of this data set. Two types of encoding methods give similar results, so I am going to show one here.
Albumin_and_Globulin_Ratio conlum has 4 missing values.
Dataset (target) has 1 and 2, which 2 means healthy.

## Explore age and gender of the patients 

**Counting the number of patients**

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig2.png)

Number of patients diagnosed with liver disease:  416
Number of patients not diagnosed with liver disease:  167
Number of patients that are female:  167
Number of patients that are male :  416

**How many patients with liver disease are female and male?**

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig3.PNG)
                Age
Dataset Gender     
Healthy Female   50
        Male    117
Sick    Female   92
        Male    324


There are more male patient records than female patients. The age distribution is similar for both gender. Some patients are as young as 4-year-old. It is unclear if the biochemistry of young people is the same as older patients.

## Explore correlation between variables

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig5.png)

Strong correlation between Direct Bilirubin and Total Bilirubin, Albumin and Total_Proteins, and Aspartate_Aminotransferase and Alamine_Aminotransferase. We might be able to drop these.

# Logistic Regresssion (Best model) [notebook](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_logistic.ipynb)

After hyperparameter tuning, I obtain about 78% accuracy. Then, I calculate feature of importance. Feature of importance for logistic regression can be obtained from coef_ attribute, or by creating a function that permute each column and see how that effect the accuracy.Columns with low feature of importances can be dropped.

These are feature of importance from logistic regression baed on coef_ attribute.  

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig7.png)

In this case, dropping low importance features does not drastically improve the accuracy. I end up with about 78% accuracy. 

This is the confusion matrix. 

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig8.png)

# Random Forest Classifier [notebook](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients_random_forest.ipynb) 

After hyperparameter tuning, I obtain about 72% accuracy. Then, I calculate feature of importance.

These are feature of importance from random forest model 

![](https://github.com/worasom/indian_liver_patients/blob/master/figgit/fig6.png)

From the dendogram, there are strong correlation between Direct Bilirubin and Total Bilirubin, Albumin and Total_Proteins, and Aspartate_Aminotransferase and Alamine_Aminotransferase. The middle two were already dropped due to low feature of importance. At the end, I use Total_Bilirubin, Direct_Bilirubin, Alkaline_Phosphotase, Alamine_Aminotransferase and obtain 73% Accuracy. 

# Conclusions 

Logistic regression achieved 78% accuracy on the validation set (less over fittign compared to random forest) Features included in the models are 'Alamine_Aminotransferase', 'Direct_Bilirubin', 'Aspartate_Aminotransferase', 'Albumin', 'Total_Protiens','Alkaline_Phosphotase', 'Age','Albumin_and_Globulin_Ratio'. The logistic regression and random forest has large false positive.

Note: using neural network is not better to a small dataset.
