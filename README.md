# Marketing-Campaign-Success-Estimation-Model

Pre-processing Steps 

Before training the Random Forest model, I applied a set of preprocessing steps to get the data into shape.
All the steps were designed to be fully compatible with how Random Forest works — no assumptions about linearity, but still clean and meaningful data.
This included cleaning, feature engineering, handling missing values, dropping noisy columns, and encoding categoricals. Basically, making sure the model has everything it needs to learn effectively 

-------------------------------------------------------------------------------------------------------------------

Modeling Steps 

I built the model in three versions:
1.	Default model – with standard parameters
2.	Importance-based model – trained using all features
3.	Optimized model – focused only on the most impactful variables
For each version, I evaluated performance using Gini, Precision, and Recall 
In the optimized model, I only kept features with importance above 5% — keeping it clean, relevant, and effective.

--------------------------------------------------------------------------------------------------------------------

Random Forest Classification with Feature Importance Selection 

After training the initial Random Forest model, I analyzed feature importances to understand which variables were truly making an impact.
I selected only those independent features that:
•	Had an importance score above 10%
•	Did not cause overfitting (i.e., had balanced train vs. test performance)
Then, I rebuilt the model using just these strong features — resulting in a more focused, efficient, and interpretable classifier 

---------------------------------------------------------------------------------------------------------------------------------------

Hyperparameter Tuning Setup 

To improve model performance, I used RandomizedSearchCV with a custom grid of hyperparameters:
•	n_estimators: Number of trees in the forest (200 to 1000)
•	max_features: How many features to consider at each split (sqrt, 0.3, 0.5, or all)
•	max_depth: Tree depth (10 to 100)
•	min_samples_split: Min samples needed to split a node (20 or 50)
•	min_samples_leaf: Min samples at each leaf (5, 8, or 10)
This random grid helps explore different model configurations and find the most effective one without trying every possible combo 

--------------------------------------------------------------------------------------------------------------------------------------

Univariate Analysis 

Univariate analysis looks at each feature individually to see how well it explains the target variable.
It helps identify the most informative and stable predictors to include in the model 

--------------------------------------------------------------------------------------------------------------------------------------

Final Model 

The final model was built using only the most impactful features, selected based on performance and stability.
This approach ensures a model that is both accurate and efficient, without unnecessary complexity 

---------------------------------------------------------------------------------------------------------------------------------------
Deployment 

Using the final trained model, I calculated the probability of interest for each record in the test_data 
Only the features the model was trained on were used — ensuring consistency and reliable predictions 
This step prepares the results for real-world use — whether it’s decision-making, reporting, or further action 
