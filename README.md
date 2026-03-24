# Data-Science-Personal-Project
A good beginner Data Science project with practical Python code on data loading, cleaning, analysis, and visualization
•	Loading CSV files with pandas
•	Data exploration
•	Summary statistics
•	Data visualization
loading the data set
import pandas as pd
df = pd.read_csv("student_performance.csv", delimiter=';')
df = df.drop(0, axis=0)
df.columns = ["Student ID", "Study Hours", "Attendance", "Sleep Hours", "Exam Score"]
#df.head(100)
pd.set_option('display.max_row', 100)
df.head(100)
df.isnull().sum()
#stats
df.describe()
Working with correlation
df.corr(numeric_only=True)
filling the missing gabs with mean value
df = df.fillna(df.select_dtypes(include='number').mean().round(0))
df.head(100)
Calculating mean_score, max_score & min_score

mean_score = np.array(df['Exam Score']).mean()
print("The mean value of exam score is:", mean_score)

max_score = np.array(df['Exam Score']).max()
print("The maximun exam score is:", max_score)

min_score = np.array(df['Exam Score']).min()
print("The miniimun exam score is:", min_score)
Ploting Histogram of Exam Scores
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
fig = plt.figure(figsize=(15,7.5))
df['Exam Score'].hist(bins=10)
plt.xlabel("Exam Scores")
plt.title("Distribution of Exam Scores")

# calculating statistics data
data = df['Exam Score']
min_value = np.min(data)
max_value = np.max(data)
mid_value = np.mean(data)
med_value = np.median(data)
mod_value = data.mode()[0]

#DISPLAYING A STATISTICS VALUE AT RIGHT TOP SIDE OF THE CHART
#checking axis limits
xmin, xmax = plt.xlim()
ymin, ymax = plt.ylim()

# top-right position
x = xmax - (xmax - xmin) * 0.02
y = ymax * 0.95

# vertical lines
plt.axvline(x=min_value, color='red', label='Min')
plt.axvline(x=mid_value, color='green', label='Mean')
plt.axvline(x=max_value, color='black', label='Max')
plt.axvline(x=mod_value, color='gray', label='Mode')
plt.axvline(x=med_value, color='pink', linestyle='--', label='Median')

# statistics text
stats_text = f'''
Min: {min_value:.2f}
Mean: {mid_value:.2f}
Median: {med_value:.2f}
Mode: {mod_value:.2f}
Max: {max_value:.2f}
'''

plt.text(x, y, stats_text, ha='right', va='top', bbox=dict(facecolor='white'))
plt.legend()
plt.show()
Ploting of Scatter plot (Study Hours vs Score)


plt.scatter(df["Study Hours"], df["Exam Score"])
plt.xlabel("Study Hours")
plt.ylabel("Exam Score")
plt.plot(df['Study Hours'], df['Exam Score'])
plt.show()
Creating Boxplot of scores
plt.boxplot(df['Exam Score'])

plt.show()
df.loc[20,'Exam Score']=0
plt.boxplot(df['Exam Score'])
plt.show()
plt.bar(df["Study Hours"], df["Exam Score"])
plt.ylabel("Exam Score")
plt.xlabel("Study Hours")
plt.title("Relationship between Study Hours and Exam Score")
plt.show()
