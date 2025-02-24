# 📊 Python Module End Project - ABC Company Employee Analysis  

## 📌 Project Overview  
This project analyzes employee data from **ABC Company**, focusing on **team distribution, position segregation, age groups, salary expenditure, and correlations between salary and age**.  
The dataset contains **458 rows and 9 columns**, and we use Python libraries like **Pandas, NumPy, Matplotlib, and Seaborn** for data analysis and visualization.  

---

## 📂 Files in this Repository  
- **`ABC_company_data_processed.csv`** → Processed dataset with cleaned data.  
- **`Employee_Analysis.ipynb`** → Jupyter Notebook with all code & visualizations.  
- **`README.md`** → Project documentation and steps.  

---

## 📊 Data Analysis & Visualizations  

This section provides **five key visualizations** to understand employee distribution, salary insights, and correlations.  

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

# 📌 1️⃣ Bar Chart for Team Distribution  
team_distribution = df["Team"].value_counts(normalize=True) * 100  
plt.figure(figsize=(10, 6))  
sns.barplot(x=team_distribution.index, y=team_distribution.values, palette="viridis")  
plt.xlabel("Teams")  
plt.ylabel("Percentage of Employees (%)")  
plt.title("Team Distribution in the Company")  
plt.xticks(rotation=45)  
plt.show()  

# 📌 2️⃣ Pie Chart for Position Segregation  
position_distribution = df["Position"].value_counts()  
plt.figure(figsize=(8, 8))  
plt.pie(position_distribution, labels=position_distribution.index, autopct='%1.1f%%', startangle=140,  
        colors=['skyblue', 'lightgreen', 'salmon', 'gold', 'violet'])  
plt.title("Position Distribution in Company")  
plt.axis("equal")  
plt.show()  

# 📌 3️⃣ Bar Chart for Age Distribution  
df["Age_Group"] = pd.cut(df["Age"], bins=[20, 30, 40, 50, 60], labels=["20-30", "30-40", "40-50", "50-60"])  
age_group_counts = df["Age_Group"].value_counts()  
plt.figure(figsize=(8, 5))  
age_group_counts.plot(kind="bar", color="skyblue", title="Age Group Distribution")  
plt.xlabel("Age Group")  
plt.ylabel("Number of Employees")  
plt.show()  

# 📌 4️⃣ Bar Chart for Salary Distribution by Team & Position  
team_salary = df.groupby("Team")["Salary"].sum().sort_values(ascending=False)  
position_salary = df.groupby("Position")["Salary"].sum().sort_values(ascending=False)  

fig, axes = plt.subplots(1, 2, figsize=(14, 6))  

axes[0].bar(team_salary.index, team_salary.values, color='skyblue')  
axes[0].set_title("Total Salary Expenditure by Team")  
axes[0].set_xlabel("Teams")  
axes[0].set_ylabel("Total Salary")  
axes[0].tick_params(axis='x', rotation=45)  

axes[1].bar(position_salary.index, position_salary.values, color='salmon')  
axes[1].set_title("Total Salary Expenditure by Position")  
axes[1].set_xlabel("Positions")  
axes[1].set_ylabel("Total Salary")  
axes[1].tick_params(axis='x', rotation=45)  

plt.tight_layout()  
plt.show()  

# 📌 5️⃣ Scatter Plot for Age vs Salary Correlation  
plt.figure(figsize=(8, 5))  
sns.scatterplot(x=df["Age"], y=df["Salary"], hue=df["Team"], palette="Set1", alpha=0.7)  
plt.title("Age vs Salary Correlation by Team")  
plt.xlabel("Age")  
plt.ylabel("Salary")  
plt.legend(title="Team")  
plt.show()  
📊 Key Insights & Findings
✔ Sales & Engineering Teams have the highest number of employees.
✔ Managerial Positions have the highest salary expenditure.
✔ Employees aged 30-40 form the largest group.
✔ There is a positive correlation between age and salary (older employees earn more).
✔ Salary varies significantly by team and position.

🚀 Technologies Used
Python 🐍
Pandas 📊
NumPy 🔢
Matplotlib 📈
Seaborn 🎨
Jupyter Notebook 📒
