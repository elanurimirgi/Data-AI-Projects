**Software Engineer Salaries UCB Algorithm Project** <br/>
*Overview* <br/>
This project applies a machine learning and data analysis workflow to a dataset containing software engineer salary information. The dataset includes features like the company score, job title, location, and salary range, among others. The goal is to predict suitable job listings based on company scores and salary estimates using the Upper Confidence Bound (UCB) algorithm, a well-known method in reinforcement learning.

*The following techniques were applied:* <br/>

Data preprocessing (handling missing values, extracting salary ranges)
Feature engineering (one-hot encoding for categorical features)
Data normalization
UCB algorithm implementation
Dataset Columns
Company: The hiring company
Company Score: The average rating of the company as provided by Glassdoor
Job Title: The title of the software engineering position
Location: The job's location
Date: The date the job was posted
Salary: The estimated salary range for the position, in the form of ranges like "$68K-$94K (Glassdoor est.)"
Project Workflow



**1. Data Preprocessing** <br/>
Loading and Inspecting the Dataset: The dataset is loaded into a pandas DataFrame. Missing values and data types are analyzed using the `isnull()` and dtypes functions.

Salary Extraction: A custom function `extract_salary()` is used to extract the salary range and convert it into a numerical average. The salary strings (e.g., "$68K-$94K") are transformed into two new columns:

Average Salary: The average of the salary range.
Estimate Type: Indicates whether the salary is an "Employer est." or "Glassdoor est."
Handling Outliers: Interquartile Range (IQR) is used to detect outliers in the "Average Salary" column. Outliers are flagged, and their count is printed.

Imputing Missing Values: The K-Nearest Neighbors (KNN) Imputer is applied to fill missing values in the Company Score and Average Salary columns. The imputation is done using 2 nearest neighbors.

One-Hot Encoding: The Job Title column is one-hot encoded using the OneHotEncoder. This converts the categorical job titles into binary columns representing each unique job title.

Data Normalization: The Company Score and Average Salary columns are normalized using MinMaxScaler to scale the values between 0 and 1.



**2. Upper Confidence Bound (UCB) Algorithm** <br/>
The UCB algorithm is applied to recommend jobs by balancing exploration and exploitation. It selects the best job titles based on the rewards (combination of normalized salary and company score).

*UCB Steps:* <br/>
Initialize the number of selections and sum of rewards for each job title.
For each iteration, calculate the upper confidence bound for each job title. The UCB balances between:
Jobs with a higher average reward (exploitation).
Jobs that haven’t been selected often yet (exploration).
Select the job title with the highest upper bound.
Update the count and reward for the selected job title.
The reward is a combination of the Company Score and normalized Salary, with the formula:

`reward = Company Score + (Average Salary / 100000)`



**3. Results** <br/>
The UCB algorithm is run on the training and test datasets. The results are stored in two separate DataFrames:

`train_results_df`: Displays the selection count and total rewards for each job title during training.
`test_results_df`: Displays the selection count and total rewards for each job title during testing.



**4. Output** <br/>
The results of the UCB algorithm provide insight into:

Which job titles are most recommended based on the highest combination of Company Score and Salary.
How often each job title is selected and its corresponding total reward during both training and testing.
Instructions to Run the Project
Install Required Libraries:

`pip install numpy pandas scikit-learn matplotlib`
Run the Python Script: The project is written in Python and relies on the following libraries:

pandas: For data manipulation.
NumPy: For numerical computations.
scikit-learn: For machine learning tasks (KNN imputation, one-hot encoding, and scaling).
matplotlib: For any optional visualization needs.
To run the script, use:

`python script_name.py`
Expected Output: The output will consist of two DataFrames:

`train_results_df`: Shows the selection count and total reward for each job title during the training phase.
`test_results_df`: Shows the selection count and total reward for each job title during the testing phase.
Conclusion
This project demonstrates the application of the Upper Confidence Bound (UCB) algorithm to recommend jobs based on company scores and salary. The workflow also covers essential data preprocessing steps like handling missing values, one-hot encoding, and data normalization.

Future Improvements:
Incorporating additional features, such as location or job posting date, could improve the recommendation system.
Experimenting with different reinforcement learning algorithms like Thompson Sampling.

**NOTE** </br>
If you want to contribute to my project you can contact me
