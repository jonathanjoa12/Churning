# Customer Churning

Order of Notebook to be Ran:
1) Exploratory Data Analysis (EDA)
2) Preprocessing
3) Modeling

The Data Source: Kaggle

Problem Statement: 

Customer Relationship Management (CRM) is an important strategy for businesses that consistently build, strengthen, and manage customer relationships for a long period of time. An important reason to maintain business-customer relationship is that the cost of acquiring a customer is higher than the cost of maintaining a loyal customer base. Churning models are consistently developed to identify any potential early churners and to predict customers that are likely to commit acts of churning on their own. There are several factors that result in customer churning that include but are not limited to: low customer satisfaction, competition from other companies providing similar services, inflation of prices, etc. 

Exploratory Data Analysis for the customer dataset:

The variable we want to predict in this dataset is the attrition flag. In other words, whether the customer remains loyal to the bank or not. After doing a value count for the attrition flag, the attrition count is significantly imbalanced. Only 16% of the data represents the customer having an attrition flag of 1 meaning the customer did not remain loyal to the company and committed the act of churning. Therefore, during the data preprocessing aspect of this project, there must be data solutions implemented to deal with the imbalanced data. 

Many of the variables in our data are not one hot encoded. When building any model based off a dataset, all variables must be numerical. Therefore, a function was constructed to make sure all categorical features were represented numerically. 

Visualizations: Some features are represented through graphs.

-	Heatmap
After constructing the heatmap representing the correlations of all features throughout the dataset, we notice that the top three variables with the highest correlation to the attrition flag are the contact count, the number of months inactive, and the number of dependents. 

-	Histograms/distplots
Histograms are used to represent all the features in our dataset. What we notice especially in features including the card category, credit limit, open to buy credit line, total transaction amount, and the average utilization ratio is that the data is skewed. Therefore, we will need to consider multiple data solutions including implementing power transformers throughout the preprocessing stage. 


Preprocessing and Model Selection

Predictions: 

-	SMOTE: 
Synthetic Minority Oversampling Technique (SMOTE) was used due to the presence of imbalanced data. Before using the technique, churned customers represented only about 16% of our data. After using the technique, it represented exactly half of our dataset. 

-	Powertransforming and train-test splitting:
Our data is skewed; therefore we want to perform a method to our datasets to reduce this. After powertransforming our dataset, we train test split our data to see how well our data generalizes to future data. 
 

Modeling and Results:

The type of model used to represent this data involves classifiers.

The types of models that were compared throughout the project include logistic regression, Decision Trees, Random Forests, ExtraTrees, Gradient Boosting Models, Support Vector Machines, Support Vector Machines with AdaBoost, Feed-Forward Neural Networks. These models are the most widely used for regression models and tend to result in better scores. The metrics that are primarily involved to evaluate regression modeling are R squared scores and root mean squared errors.

-	The Logistic Regression Model: The logistic regression produced accuracy train and test scores of .82 and .91 respectively. The F1 score is .68. 

-	KNN Model: K-Nearest-Neighbor model produced an accuracy train score of .95 and test score of .87. The F1 score is .68

-	Decision Trees: Decision Tree model produced an accuracy train score of 1 and test score of .90. The F1 score is .66

-	RandomForests: Random Forests model produced an accuracy train score of 1 and test score of .95. The F1 score is .76

-	ExtraTrees: Extra Trees model produced an accuracy train score of 1 and test score of .93. The F1 score is .86

-	Gradient Boosting: GradientBoosting produced an accuracy train score of .98 and a test score of .92. The F1 score is .88

-	SVMS: SVMs produced an accuracy train score of .96 and a test score of .92. The F1 score is .78

-	SVMS with AdaBoost: SVMs with AdaBoost produced a accuracy train score of .79 and a test score of .77. The F1 score is .58.




Analysis of our models.
- One important consideration when analyzing the models in general is the bias-variance tradeoff. We want to choose a model with an accuracy testing score that is similar or higher to the accuracy training score. If the testing score is much lower than the training score, it is an indication of the model overfitting. A cross validation testing score was also developed to get an idea of where the metrics should generally lie around. In the case of the GradientBoosting model, it has the highest F1 score of 88% with an accuracy testing score of 96%. The cross-validation testing score is approximately 96% which matches the accuracy testing score. Therefore, the GradientBoosting model would be the best model to identify potential bank churners. 

Although the Decision Trees, Random Forests, and ExtraTrees had near perfect accuracy scores, they produced lower F1 scores and their accuracy test scores were lower than their training score, resulting in an increased likelihood of overfitting.

-	Feature Importance: The highest metrics within the features are the Total Transaction Count, Total Transaction Amount, and Total Revolving Balance. 

Total Transaction Count: In the case of the dataset, the number of times a consumer has used his/her credit card since opening. This feature has the highest feature importance value being .48. 

Total Transaction Amount: The total amount of credit used since card opening. This has a feature importance value being .15.

Total Revolving Balance: The total balance the customer still must pay off. This has a feature importance value being .11 rounded up.


Conclusion: 

The model with the best chances of identifying a potential churner for this dataset would be the GradientBoosting model. It has the highest F1 score of 87% along with an accuracy testing score of 96%. 


Recommendations:

Based on the values, these three features are a likely an indicator of an incoming credit card churner. Based on common knowledge about credit cards, there are multiple reasons leading churning based on these three features. One is the total transaction count is not going up. A bank or credit card company should look at the transaction count with respect to time and analyze the patterns of the consumer. A person with a transaction amount that is not going up as time passes could be a likely candidate of churning. In addition, the same applies to total transaction amount. The total transaction amount would typically have a good correlation with transaction count because the higher the transaction count, the higher the transaction amount is. 

When looking at the total revolving balance, the bank should pinpoint those with extremely low credit card balances. One would typically close a credit card once all his/her balances are paid off or else interest would still accumulate on that unpaid balance. Therefore, all banks that would want to identify churners should narrow down all customers with low or close to 0 balances. After successfully identifying potential churners, the bank would have to get into contact with them to negotiate and prevent it from happening.

One limitation of the model is the accuracy test score is still slightly slower than the training score, indicating a sign of overfitting. 




