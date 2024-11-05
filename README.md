# Trevarious_Taylor_CYBR520_Fall24
HW 1 
# Load the dataset
data = pd.read_csv('/mnt/data/spambase(2).csv')

# Set up visual style for seaborn
sns.set(style="whitegrid")

# Exploratory Data Analysis (Visual Aids)

# 1. Line Chart: Distribution of 'capitalLong'
plt.figure(figsize=(10, 6))
plt.plot(data['capitalLong'], color='blue')
plt.title("Line Chart: Distribution of 'capitalLong'")
plt.xlabel("Index")
plt.ylabel("capitalLong")
plt.show()

# 2. Bar Chart: Frequency of 'type' (spam and nonspam)
plt.figure(figsize=(8, 6))
sns.countplot(data=data, x='type', palette='viridis')
plt.title("Bar Chart: Frequency of 'type' (Spam vs Nonspam)")
plt.xlabel("Type")
plt.ylabel("Frequency")
plt.show()

# 3. Scatter Plot: Relationship between 'num3d' and 'num000'
plt.figure(figsize=(8, 6))
plt.scatter(data['num3d'], data['num000'], alpha=0.5, color='purple')
plt.title("Scatter Plot: Relationship between 'num3d' and 'num000'")
plt.xlabel("num3d")
plt.ylabel("num000")
plt.show()

# 4. Histogram: Distribution of 'money'
plt.figure(figsize=(10, 6))
plt.hist(data['money'], bins=30, color='orange', edgecolor='black')
plt.title("Histogram: Distribution of 'money'")
plt.xlabel("money")
plt.ylabel("Frequency")
plt.show()

# 5. Pie Chart: Proportion of spam and nonspam emails
plt.figure(figsize=(8, 8))
data['type'].value_counts().plot.pie(autopct='%1.1f%%', colors=['skyblue', 'salmon'], startangle=140)
plt.title("Pie Chart: Proportion of Spam and Nonspam Emails")
plt.ylabel("")
plt.show()

# 6. Summary Statistics Table: capitalAve
capitalAve_summary = data['capitalAve'].describe()
print("Summary Statistics for 'capitalAve':\n", capitalAve_summary)

# Descriptive Statistics

# 7. Mean, Median, and Standard Deviation of 'our'
our_mean = data['our'].mean()
our_median = data['our'].median()
our_std = data['our'].std()
print("\nMean of 'our':", our_mean)
print("Median of 'our':", our_median)
print("Standard Deviation of 'our':", our_std)

# 8. Minimum and Maximum of 'hp'
hp_min = data['hp'].min()
hp_max = data['hp'].max()
print("\nMinimum of 'hp':", hp_min)
print("Maximum of 'hp':", hp_max)

# 9. 25th, 50th, and 75th Percentiles for 'telnet'
telnet_percentiles = data['telnet'].quantile([0.25, 0.5, 0.75])
print("\nPercentiles of 'telnet':\n", telnet_percentiles)

# 10. Mode of 'you'
you_mode = data['you'].mode().iloc[0]
print("\nMode of 'you':", you_mode)

# 11. Interquartile Range (IQR) for 'business'
business_iqr = data['business'].quantile(0.75) - data['business'].quantile(0.25)
print("\nInterquartile Range (IQR) of 'business':", business_iqr)

# 12. Skewness and Kurtosis of 'credit'
credit_skewness = skew(data['credit'])
credit_kurtosis = kurtosis(data['credit'])
print("\nSkewness of 'credit':", credit_skewness)
print("Kurtosis of 'credit':", credit_kurtosis)

# 13. Correlation Coefficient between 'capitalAve' and 'capitalTotal'
capitalAve_capitalTotal_corr = data['capitalAve'].corr(data['capitalTotal'])
print("\nCorrelation between 'capitalAve' and 'capitalTotal':", capitalAve_capitalTotal_corr)

# 14. Range of values for 'num857'
num857_range = data['num857'].max() - data['num857'].min()
print("\nRange of 'num857':", num857_range)

# 15. Variance of 'money'
money_variance = data['money'].var()
print("\nVariance of 'money':", money_variance)

# Correlation Analysis

# 16. Correlation Matrix for all numeric features
correlation_matrix = data.corr()
print("\nCorrelation Matrix:\n", correlation_matrix)

# 17. Highest Positive and Negative Correlations
sorted_correlations = correlation_matrix.unstack().sort_values(ascending=False)
highest_positive_corr = sorted_correlations[(sorted_correlations < 1) & (sorted_correlations > 0)].head(2)
highest_negative_corr = sorted_correlations[sorted_correlations < 0].head(2)
print("\nHighest Positive Correlations:\n", highest_positive_corr)
print("\nHighest Negative Correlations:\n", highest_negative_corr)

# 18. Heatmap of Correlation Matrix
plt.figure(figsize=(12, 10))
sns.heatmap(correlation_matrix, annot=False, cmap='coolwarm')
plt.title("Heatmap of Correlation Matrix")
plt.show()

# 19. Correlation between 'remove' and 'internet'
remove_internet_corr = data['remove'].corr(data['internet'])
print("\nCorrelation between 'remove' and 'internet':", remove_internet_corr)

# 20. Correlation between 'num3d' and 'num000'
num3d_num000_corr = data['num3d'].corr(data['num000'])
print("\nCorrelation between 'num3d' and 'num000':", num3d_num000_corr)

# 21. Correlation between 'font' and 'money'
font_money_corr = data['font'].corr(data['money'])
print("\nCorrelation between 'font' and 'money':", font_money_corr)

# 22. Correlation between 'table' and 'technology'
table_technology_corr = data['table'].corr(data['technology'])
print("\nCorrelation between 'table' and 'technology':", table_technology_corr)
