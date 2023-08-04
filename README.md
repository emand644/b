# b
import pandas as pd

data = {
    'age': [39, 50, 38, 53, 28],
    'workclass': ['State-gov', 'Self-emp-not-inc', 'Private', 'Private', 'Private'],
    'fnlwgt': [77516, 83311, 215646, 234721, 338409],
    'education': ['Bachelors', 'Bachelors', 'HS-grad', '11th', 'Bachelors'],
    'education-num': [13, 13, 9, 7, 13],
    'marital-status': ['Never-married', 'Married-civ-spouse', 'Divorced', 'Married-civ-spouse', 'Married-civ-spouse'],
    'occupation': ['Adm-clerical', 'Exec-managerial', 'Handlers-cleaners', 'Handlers-cleaners', 'Prof-specialty'],
    'relationship': ['Not-in-family', 'Husband', 'Not-in-family', 'Husband', 'Wife'],
    'race': ['White', 'White', 'White', 'Black', 'Black'],
    'sex': ['Male', 'Male', 'Male', 'Male', 'Female'],
    'capital-gain': [2174, 0, 0, 0, 0],
    'capital-loss': [0, 0, 0, 0, 0],
    'hours-per-week': [40, 13, 40, 40, 40],
    'native-country': ['United-States', 'United-States', 'United-States', 'United-States', 'Cuba'],
    'salary': ['<=50K', '<=50K', '<=50K', '<=50K', '<=50K']
}

df = pd.DataFrame(data)


# Assuming you have already created the DataFrame 'df' using the data provided earlier

# Calculate the average age of men
average_age_men = df[df['sex'] == 'Male']['age'].mean()

print("Average age of men:", average_age_men)

bachelor_count=df[df['education']=='Bachelors'].shape[0]
Total_people=df.shape[0]
precntage_batchelor=(bachelor_count/Total_people)*100


# Assuming you have already created the DataFrame 'df' with the given dataset.

# Filter rows with advanced education
advanced_education = df[df['education'].isin(['Bachelors', 'Masters', 'Doctorate'])]

# Calculate the percentage of people with advanced education making more than 50K
percentage_advanced_education_rich = (advanced_education['salary'] == '>50K').mean() * 100

print("Percentage of people with advanced education making more than 50K:", percentage_advanced_education_rich)
#What is the minimum number of hours a person works per week?
minum_salary=df['hours-per-week']
print("smallest element is", min(minum_salary))
high_income = df[df['salary'] == '>50K']

if not high_income.empty:
    # Find the most popular occupation for high-income individuals
    most_popular_occupation = high_income['occupation'].value_counts().idxmax()
    print("Most popular occupation for those who earn >50K:", most_popular_occupation)
else:
    print("There are no high-income individuals in the dataset.")
