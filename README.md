### DEVELOPED BY: SABARI S
### REGISTER NO: 212222240085
### DATE:


# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES

# AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000
data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.
3. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
4. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000
data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.
5. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.

# PROGRAM:
```python
import pandas as pd
from matplotlib import pyplot as plt
from pandas.plotting import autocorrelation_plot
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
import numpy as np
import warnings
warnings.filterwarnings('ignore')

# Load your dataset
file_path = 'data_date.csv'  # Replace with the correct file path
data = pd.read_csv(file_path)

# Convert 'Date' column to datetime and set it as the index
data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)

# Select a specific country's AQI Value, for example, 'India'
country_data = data[data['Country'] == 'India']['AQI Value']

# Resample the AQI values by day to get daily data (you can modify if necessary)
daily_data = country_data.resample('D').mean().dropna()

# Simulating an ARMA(1,1) Process
ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=1000)

plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process')
plt.xlim([0, 200])
plt.show()

plot_acf(ARMA_1)
plot_pacf(ARMA_1)
plt.show()

# Simulating an ARMA(2,2) Process
ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=1000)

plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process')
plt.xlim([0, 200])
plt.show()

plot_acf(ARMA_2)
plot_pacf(ARMA_2)
plt.show()




```


# OUTPUT:
## SIMULATED ARMA(1,1) PROCESS:


![image](https://github.com/user-attachments/assets/84f45371-1914-4698-ac40-dec07d8a7f69)


## Partial Autocorrelation



![image](https://github.com/user-attachments/assets/338a8915-8d14-44a8-99a0-bc2924d36030)

## Autocorrelation

![image](https://github.com/user-attachments/assets/944405ec-cf2e-43ea-96a7-17c6d253876e)



## SIMULATED ARMA(2,2) PROCESS:

![image](https://github.com/user-attachments/assets/55ab7520-a591-40be-a584-b9bb46d86712)

## Partial Autocorrelation

![image](https://github.com/user-attachments/assets/87eb9c01-96eb-4f24-846c-32a23d40f089)


## Autocorrelation

![image](https://github.com/user-attachments/assets/7463c500-b4a3-42c6-b229-b8b4fd139873)

# RESULT:
Thus, a python program is created to fit ARMA Model for Time Series successfully.
