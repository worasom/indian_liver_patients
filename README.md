# Indian Liver Patients Data
Automatic liver patients identification from their blood test data. This is a kaggle[https://www.kaggle.com/uciml/indian-liver-patient-records/home] competition. The data is from Lichman, M. (2013). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.

Compare performance of [random forest](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients_random_forest.ipynb), [logistic regression](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_logistic.ipynb), and [neural network](https://github.com/worasom/indian_liver_patients/blob/master/Indian_liver_patients-NN.ipynb) on identifying liver patients from their blood panel. The traing procedures for each model can be found in the hyperlink.  

There are a number of machine learning papers that work on this data set;for example:
- Bendi Venkata Ramana, Prof. M. S. Prasad Babu and Prof. N. B. Venkateswarlu, "A Critical Comparative Study of Liver Patients from USA and INDIA: An Exploratory Analysis", International Journal of Computer Science Issues, (May 2012)
- Bendi Venkata Ramana and Prof. M.Surendra Prasad Babu, "Liver Classification Using Modified Rotation Forest" International Journal of Engineering Research and Development,  (June 2012)

Skills 

- Exploratory data analysis and feature engineering using Python (pandas, numpy, matplot. pyplotlib).
- Experimented with different models (Logistic regression,  random forest classifier, K-nearest neighbors, neural network) using Python (scikit-learn, pytorch, fastai)
- Hyper parameter tuning with randomsearchCV (scikit-learn)
- Calculate feature of importance
- Achieve 78% accuracy on the validation set(baseline = 72%) , loss =  0.47(baseline 0.69) 
