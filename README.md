### Developed By : M Sanjay
### Reg. NO . 212222240090
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the India's GDP and Change in Annual Percentage Change.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python

# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
  # Replace with the correct path to your file
df = pd.read_csv('india-gdp.csv')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'date' column to datetime and setting it as the index
df['date'] = pd.to_datetime(df['date'], format='%Y-%m-%d')
df.set_index('date', inplace=True)

# Filling missing values for the "tank" column (if any) using forward fill
df['AnnualChange'] = df['AnnualChange'].fillna(method='ffill')

# Performing seasonal decomposition on the "tank" feature (additive model)
decomposition = seasonal_decompose(df['AnnualChange'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()

```
### OUTPUT:
FIRST FIVE ROWS:

![Screenshot 2024-09-23 104448](https://github.com/user-attachments/assets/b92cf3dd-86b0-450b-a800-22d366ff9e15)

SEASONAL PLOT REPRESENTATION :

![Screenshot 2024-09-23 104531](https://github.com/user-attachments/assets/369876a5-39a1-414c-aa0c-6e566e272bb8)

TREND PLOT REPRESENTATION :

![Screenshot 2024-09-23 104516](https://github.com/user-attachments/assets/f2c908f1-64a2-4598-b6b5-5fd187bdb3e1)

PLOTTING THE DATA:

![Screenshot 2024-09-23 104547](https://github.com/user-attachments/assets/6330f7e0-125e-4d67-a0a4-decf2991f953)

OVERAL REPRESENTATION:

![Screenshot 2024-09-23 104506](https://github.com/user-attachments/assets/22088370-0263-496a-b9c1-39a3b93f6a05)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
