# LendingClub-Loan-Portfolio-Optimization-Project

Overview

This project focuses on analyzing historical LendingClub loan data to develop a robust and optimized investment strategy for peer-to-peer lending. Using both classification and regression models, we predict loan defaults and returns, creating a risk-adjusted strategy that optimizes portfolio performance.

We employed machine learning models, such as L1 and L2 Penalized Logistic Regression, Decision Trees, Random Forest Classifiers, Lasso-Lars Regressor, Ridge Regressor, Ordinary Least Squares Regressor, and more. Additionally, the project tests different optimization strategies to minimize risk and maximize returns for investors.

Project Highlights

	•	Extensive Exploratory Data Analysis (EDA): Performed in-depth analysis to understand loan features, distributions, and missing data.
	•	Training and Testing Data Splits: Randomly selected rows within data segments to create balanced training and testing datasets.
	•	Downsampling for Balanced Classes: Downsampled dataset to equalize the classification categories (Default vs. Non-Default Loans).
	•	Model Selection: Utilized a range of classification and regression models for default prediction and return estimation, selecting the best-performing models.
	•	Portfolio Strategy Testing: Ran models across different portfolio sizes to gauge robustness.
	•	Optimization: Applied Docplex to optimize portfolio returns considering both returns and risk aversion, ensuring risk-adjusted profitability.

Table of Contents

	1.	Exploratory Data Analysis (EDA) and Preprocessing
	2.	Data Segmentation and Random Row Selection
	3.	Downsampling for Class Balance
	4.	Classification Model Comparison
	5.	Regression Model Comparison
	6.	Two-Stage Portfolio Strategy
	7.	Portfolio Size and Strategy Robustness
	8.	Optimization Strategies Using Docplex
	9.	Results and Conclusion

1. Exploratory Data Analysis (EDA) and Preprocessing

We conducted a comprehensive EDA to understand the structure of the dataset, distribution of features, missing data, and correlations between predictors. Key preprocessing steps include:

	•	Handling missing values
	•	Encoding categorical variables
	•	Feature scaling where applicable
	•	Data segmentation based on key indicators (e.g., loan grade, term length)

2. Data Segmentation and Random Row Selection

Data was split into training and testing datasets using random row selection within each data segment to ensure representative distribution of loans. This segmentation ensures consistency in modeling across different loan types and minimizes bias in the test set.

3. Downsampling for Class Balance

To address the class imbalance (significantly more Non-Default Loans than Default Loans), we employed downsampling of the Non-Default class. This balanced the dataset and allowed the classifiers to better detect defaults, which is a critical aspect of risk management for peer-to-peer lending investments.

4. Classification Model Comparison

Several classifiers were tested to predict loan default. The models used include:

	•	L1 Penalized Logistic Regression
	•	L2 Penalized Logistic Regression
	•	Decision Tree Classifier
	•	Random Forest Classifier

After evaluation, we selected the L1 Penalized Logistic Regression model due to its high accuracy and Default recall rate. This model demonstrated the best performance in identifying loans that would default, which is essential for building a low-risk portfolio.

5. Regression Model Comparison

We also evaluated several regression models to predict loan return for each non-defaulted loan:

	•	Lasso-Lars Regressor
	•	Ridge Regressor
	•	Ordinary Least Squares (OLS) Regressor
	•	Random Forest Regressor

The Random Forest Regressor provided the highest R² score on the test data and was selected for its ability to accurately predict loan returns.

6. Two-Stage Portfolio Strategy

After comparing various models, we adopted a Two-Stage Strategy for its durability and consistent performance. This strategy works as follows:

	1.	Stage 1: The L1 Penalized Logistic Regression model classifies loans into Default or Non-Default categories based on probability.
	2.	Stage 2: The Random Forest Regressor predicts returns for the loans classified as Non-Default. We use a weighted average return based on the predicted default probability and corresponding predicted return.

This method combines the strengths of classification and regression to optimize both risk and return in the portfolio.

7. Portfolio Size and Strategy Robustness

We tested the robustness of the Two-Stage Strategy by varying the number of loans in the portfolio (from 300 to 3,000 loans). Results showed that:

	•	The strategy performs well with 300 to 800 loans, maintaining strong return predictions and low risk.
	•	Performance declines slightly as the portfolio size increases beyond 3,000 loans, possibly indicating an overfitting risk when portfolios become too large.

This suggests that a portfolio size of 300-800 loans is optimal for durable, consistent returns with minimized risk.

8. Optimization Strategies Using Docplex

We explored different optimization strategies using Docplex:

	•	Maximizing returns
	•	Partial investments across multiple loans
	•	Maximizing returns within a dollar budget
	•	Risk-adjusted returns using a beta coefficient for risk aversion: This strategy incorporated portfolio volatility by clustering loans using K-Means to group loans with similar standard deviations, resulting in a more risk-averse optimization approach.

The final strategy (with risk aversion) was selected for its real-world applicability and robustness in optimizing returns while considering risk.

9. Results and Conclusion

The final portfolio strategy, combining the L1 Penalized Logistic Regression classifier with the Random Forest Regressor and risk-averse optimization, performed exceptionally well. Testing showed a small error rate between the predicted optimized portfolio and actual portfolio returns, indicating strong model reliability.

This demonstrates confidence in using this optimization modeling for future loan investments, providing a balance between risk-adjusted returns and portfolio durability.

Technologies Used

	•	Python: Core language for data analysis and model implementation.
	•	Scikit-Learn: Machine learning models and evaluation metrics.
	•	Docplex: Optimization strategies for maximizing returns and minimizing risk.
	•	Pandas, NumPy, Matplotlib, Seaborn: Data handling, preprocessing, and visualization.
	•	K-Means Clustering: Used to group loans based on risk characteristics (volatility).

Conclusion

This project provides a comprehensive approach to loan portfolio optimization in peer-to-peer lending. The two-stage strategy, alongside risk-adjusted optimization, delivers a practical and reliable method to maximize returns while minimizing risk. The results underscore the importance of predictive modeling in financial decision-making, enabling investors to build robust, risk-adjusted portfolios in real-world applications.

Feel free to contact me for any questions or further information!

Author: Scott Ellsworth
Email: scottellsworth1994@gmail.com
LinkedIn: https://www.linkedin.com/in/scottellsworth0395/
