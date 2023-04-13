Practical Application Assignment 17: Comparing Classifiers
Github code:https://github.com/fuyingpku/PAIIIfinal.git

#OVERVIEW: In this practical application, we have the goal to compare the performance of the four classifiers we encountered:K Nearest Neighbor, 
Logistic Regression, Decision Trees, and Support Vector Machines. We will utilize a dataset related to marketing bank products over the telephone.

#CRISP-DM Framework To frame the task, throughout our recent practical applications we will refer back to a standard process in industry for data projects called CRISP-DM. This process provides a framework for working through a data problem. 
The first step in this application will be to read through a brief overview of CRISP-DM here. 

#Business Understanding From a business perspective, we are tasked with identifying key drivers for making a decision to subscribe or not. In the CRISP-DM overview, 
we are asked to convert this business framing to a data problem definition. Using a few sentences, reframe the task as a data task with the appropriate technical vocabulary.

#Determine Business Objectives 
(1) Background: The provided dataset contains information his dataset is a result of strategic sequence of steps and activities that promote a Portuguese banking
institution's product or service, with a specific goal to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.
(2) Business Objectives: to find the best classfiers to achieve highest accuracy to predict whether the customer will subscribe the business
(3) Data and feature analysis for all the 20 features listed below with datatype associated as well: 
Bank client data :
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
 related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
 other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
 social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

(4) Business Success Criteria: As a result of this model based analysis, the model should provide 
clear recommendations to the client what consumers would subscribe and it is very helpful for targed ad for the future run on marketing bank products over the telephone. 
Our plan is to ahieve at least 90% accuracy.

(5) Requirements, Assumptions, and Constraints: this is a practice work due Apr 17th, no legal issue with data usage. 
The assumptions are good data collection in the public database. Due to the limiation of CPU power, a fration of the features was used.

(6) Risks and Contingencies terminology: The success may rely on good analysis skillset of the performer in this case 
with all the parameters for classifiers optimized.

(7) Costs and Benefits: It is a good business model which could be used for targeted ad for banks across the world on marketing bank products over the telephone.

#Determine Data Mining Goals （1） Data Mining Goals：screen all the four classifers and optimize the feature selections, 
and calcualte the business model about the gap between the features and decision to subscribe.

（2） Data Mining Success Criteria：achieve accuracy at 90%.

#Produce Project Plan （1） Project Plan：the CRISP-DM standard protocol will be carried out, in total, 
16 hrs for data understanding/preparation/modeling/evaluation/deployment

（2） Initial Assessment of Tools and Techniques：Now that you understand your business objective, we will build a basic model to get started. Before we can do this, 
we must work to encode the data. Using just the bank information features (columns 1 - 7), the features are :job, marital, education, default, housing, loan, contact.
Next we prepare the features and target column for modeling with appropriate encoding and transformations.

Evaluate results: # now we can plot the figure to understand the correlation better/easier, 
we did not see any feature with strong coorelation to y(subsription) or each other. We build a baseline model using SVM: accuray at 89%. Similarly, using the logistic regression model which we chose 4000 iterations, same accuray was obtained.
The accuracy of the models are quite similar with Logistic Regression = 0.888; SVC = 0.888, KNeighborsClassifier = 0.871; Decision Tree = 0.871. 
Based on accuray, Logistic regression and SVC works well for this dataset. (some coding is not displayed to simplify the process)

Further improvment: 
(1) considering the feature selection: secondly, what if we want to check all the features, can we process them? we can plot the figure to
understand the correlation better/easier,we did not see any feature with strong coorelation to y(subsription) or each other. 
based on the feature screening of correlation, we found that positively related features from top 3: duration, previous, poutcome and negatively related features top 3: nr.employed, euribonr3m and pdays
bank client data: 11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
other attributes: 13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted) 14 - previous: number of contacts performed before this campaign and for this client (numeric), 15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
social and economic context attributes, 16 - emp.var.rate: employment variation rate - quarterly indicator (numeric), 19 - euribor3m: euribor 3 month rate - daily indicator (numeric) , 20 - nr.employed: number of employees - quarterly indicator (numeric)

(2) Hyperparameter tuning and grid search. All of the four models have additional hyperparameters to tune and explore. 

Access of data mining results with respect to business success creteria: In principle, a business is based on the consistency of the model, 
which is shown not overfitting in this case, the model(s) build here provided the inital analysis of the price which address the business quesiton of 
picking good features to achieve high accuracy to predict subsription decision: across all the four models, we can see training time/s showed big difference comparing 
SVM and other three models, in that, SVM is not a good choice for this dataset which contains ca. 40K samples, the accuray is also not good for SVM. The best model is
Logistic regression with test accuray slightly overperform than the train accuray, both are above 90%. It showed the highest accuray across all the models tested in this work.

Table 1: summary of four classifiers on training time, accuray. 
                 Model       Train Time(grid/s) Train Accuracy Test Accuracy
0  Logistic Regression               11           0.91          0.92
1        Decision Tree              4.4           0.90          0.90
2                  KNN               76           0.91          0.91
3                  SVM            >1000           0.89          0.89

Review process: in summary, the whole process start with overview of seven features in the dataset, 
no need to remove outliers and Nan values, using graphic and correlation function to identify what are the factors contribute/correlate 
the decision and features. During the analysis, it is noticed six features are corelated to the decision to subscribe and they were shosen for further analysis, 
although 92% accuracy was achieved in LR model, but we admit there is still room to improve with a much larger dataset.

#Plan deployment: it is a general procedure used to identify and create the model in this case. all the parameters were 
fixed for any repeat needed. The model itself is ready for deployment and for sure training and interface could be employed for the customers and other dataset with same features.

#Produce final report: In this project, we screened all the features, based on the avaiablity of the dataset, 
we narrow down factors:  we found that positively related features from top 3: duration, previous, poutcome and negatively related features top 3: nr.employed, euribonr3m and pdays
bank client data: 11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
other attributes: 13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted) 14 - previous: number of contacts performed before this campaign and for this client (numeric), 15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
social and economic context attributes, 16 - emp.var.rate: employment variation rate - quarterly indicator (numeric), 19 - euribor3m: euribor 3 month rate - daily indicator (numeric) , 20 - nr.employed: number of employees - quarterly indicator (numeric)
In the regression analysis, it is found that Logistic Regression provided best prediction accuracy in the test dataset and with decent training time. 


#Review project: The initial analysis and data prep went well. However, the model still has improvment on the accuray. That could be improved with better model 
e.g. AI based model and larger dataset with more features could be selected. A group discussion could be beneficial across the class.


