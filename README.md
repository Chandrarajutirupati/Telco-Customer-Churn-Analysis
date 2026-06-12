📊 Telco Customer Churn Analysis
Project Overview
Customer churn refers to customers who stop using a company's services. Customer retention is one of the most important business challenges in the telecommunications industry. This project analyzes customer behavior and builds a machine learning model to predict whether a customer is likely to churn.
The project uses the Telco Customer Churn dataset and applies data preprocessing, feature engineering, machine learning, and model evaluation techniques to identify customers at risk of leaving the company.


🎯 Objectives
Analyze customer churn patterns.
Identify factors that influence customer retention.
Build a predictive machine learning model.
Evaluate model performance using classification metrics.
Generate business insights that can help reduce customer churn.


📁 Dataset Information
The dataset contains customer information such as:
Gender

Senior Citizen Status

Partner

Dependents

Tenure

Phone Service

Internet Service

Online Security

Device Protection

Tech Support

Streaming Services

Contract Type

Payment Method

Monthly Charges

Total Charges

Churn Status

Target Variable

Churn

Yes = Customer Left

No = Customer Stayed




🛠 Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Scikit-Learn

Jupyter Notebook




📊 Data Preprocessing
The following preprocessing steps were performed:
1. Handling Missing Values
Checked for missing values.
Cleaned and converted data types where necessary.

2. Encoding Categorical Variables
Most columns contained categorical values such as:
Plain text

Gender

Contract

InternetService

PaymentMethod

These were converted into numerical values using Label Encoding.

Python

from sklearn.preprocessing import LabelEncoder



labelencoder = LabelEncoder()

for col in categorical_cols:
    df[col] = labelencoder.fit_transform(df[col])


3. Feature Selection

Customer ID was removed because it does not contribute to churn prediction.

Python

X = dataset.drop(['customerID', 'Churn'], axis=1)

y = dataset['Churn']



4. Train-Test Split

The dataset was divided into:
Training Data (80%)
Testing Data (20%)
Python
train_test_split(X, y, test_size=0.2, random_state=0)


5. Feature Scaling
Standardization was applied using StandardScaler.
Python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
Feature scaling transforms data to:
Mean = 0
Standard Deviation = 1
This helps machine learning algorithms perform efficiently.



🤖 Machine Learning Model
Random Forest Classifier
Random Forest is an ensemble learning algorithm that combines multiple decision trees to improve prediction accuracy and reduce overfitting.
Python
from sklearn.ensemble import RandomForestClassifier

clf = RandomForestClassifier()

clf.fit(X_train, y_train)
Prediction
Python
y_pred = clf.predict(X_test)



📈 Model Evaluation
Accuracy Score
Python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)
Result
Plain text
Model Accuracy = 78%
The model correctly predicted customer churn status for approximately 78% of customers in the test dataset.




📉 Confusion Matrix
A confusion matrix was used to evaluate classification performance.
Python
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)
The confusion matrix helps identify:
True Positives
True Negatives
False Positives
False Negatives
and provides deeper insight into prediction quality.




🔍 Key Insights
1. Contract Type Matters
Customers with month-to-month contracts tend to churn more frequently compared to customers with long-term contracts.
2. Tenure Influences Retention
Customers with shorter tenure are more likely to leave the service.
3. Monthly Charges Impact Churn
Higher monthly charges are associated with increased churn rates.
4. Value-Added Services Improve Retention
Customers using services such as:
Online Security
Tech Support
Device Protection
show lower churn tendencies.
5. Internet Service Type Plays a Role
Different internet service plans demonstrate different churn patterns.




📊 Business Impact
This model can help telecommunication companies:
Identify high-risk customers.
Improve customer retention strategies.
Reduce revenue loss caused by customer churn.
Design personalized offers and loyalty programs.
Improve customer satisfaction.





In this project, customer churn data was analyzed and preprocessed using Python and Scikit-Learn. A Random Forest Classifier was trained to predict customer churn and achieved approximately 78% accuracy on the test dataset. The analysis revealed important factors affecting churn, including contract type, tenure, monthly charges, and support-related services. The developed model can assist telecommunication companies in proactively identifying customers likely to leave and implementing retention strategies to improve business performance.
