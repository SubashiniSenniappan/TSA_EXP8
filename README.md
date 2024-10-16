# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
# Developed by Subashini S
# reg no:212222240106
### Date: 


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```
# Step 1: Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Step 2: Read the weather classification dataset
file_path = '/content/weather_classification_data.csv'
data = pd.read_csv(file_path)

# Step 3: Display the shape and the first 20 rows of the dataset
print(f"Dataset Shape: {data.shape}")
print(data.head(20))

# Step 4: Set figure size for plots
plt.figure(figsize=(10, 6))

# Step 5: Suppress warnings for smooth execution
warnings.filterwarnings("ignore")

# Assuming the dataset has a 'Temperature' column to use as a time series
# Using Temperature as the 'Value' column for moving average and smoothing
data['Value'] = data['Temperature']

# Step 6: Plot the first 50 values of the 'Value' column
plt.plot(data['Value'][:50], label='Original Data')
plt.title('Original Data - First 50 Values')
plt.xlabel('Index')
plt.ylabel('Value (Temperature)')
plt.legend()
plt.show()

# Step 7: Perform rolling average transformation with a window size of 5
rolling_avg_5 = data['Value'].rolling(window=5).mean()
print("\nFirst 10 values of the rolling mean with window size 5:")
print(rolling_avg_5.head(10))

# Step 8: Perform rolling average transformation with a window size of 10
rolling_avg_10 = data['Value'].rolling(window=10).mean()

# Step 9: Create a new figure for plotting the rolling average
plt.figure(figsize=(10, 6))
plt.plot(data['Value'][:50], label='Original Data')
plt.plot(rolling_avg_5[:50], label='Rolling Mean (Window 5)', color='orange')
plt.plot(rolling_avg_10[:50], label='Rolling Mean (Window 10)', color='green')
plt.title('Moving Average - Original Data and Rolling Mean')
plt.xlabel('Index')
plt.ylabel('Value (Temperature)')
plt.legend()
plt.show()

# Step 10: Perform Exponential Smoothing
exp_smoothing = ExponentialSmoothing(data['Value'], trend='additive', seasonal=None, initialization_method="estimated")
exp_fit = exp_smoothing.fit()

# Plot the exponential smoothing result
plt.figure(figsize=(10, 6))
plt.plot(data['Value'][:50], label='Original Data')
plt.plot(exp_fit.fittedvalues[:50], label='Exponential Smoothing', color='red')
plt.title('Exponential Smoothing - Original Data and Smoothed Values')
plt.xlabel('Index')
plt.ylabel('Value (Temperature)')
plt.legend()
plt.show()

# Display the first few smoothed values
print("\nFirst 10 smoothed values from Exponential Smoothing:")
print(exp_fit.fittedvalues.head(10))
```
### OUTPUT:
![Screenshot 2024-10-16 134227](https://github.com/user-attachments/assets/70744bb3-c6f1-42bb-96ad-3e8222dfa702)

![Screenshot 2024-10-16 134227](https://github.com/user-attachments/assets/5d6e316e-1cb7-45bd-b1f4-aae5ca0a4349)

![Screenshot 2024-10-16 134246](https://github.com/user-attachments/assets/0d9d547e-d328-49fc-9cef-a5114c51bff7)

![image](https://github.com/user-attachments/assets/c5ee2918-74d3-403b-8723-31f65e9064bb)

![Screenshot 2024-10-16 134417](https://github.com/user-attachments/assets/2c6cbcdd-ee13-4413-8633-ada3994acd99)

![image](https://github.com/user-attachments/assets/3edc15bf-6d77-4368-b7de-a177e1ed3a6a)

![image](https://github.com/user-attachments/assets/1c4a8358-f63d-4829-a0d9-2c5e5c855ced)

![Screenshot 2024-10-16 134516](https://github.com/user-attachments/assets/f8596a79-a5bf-4522-9cdb-7c4496f21f1f)


### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
