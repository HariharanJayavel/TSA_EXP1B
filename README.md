# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 17.08.2025

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```c
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv('/content/Crypto Data Since 2015.csv')
data['Date']=pd.to_datetime(data['Date'])
data.set_index('Date',inplace=True)

data['Bitcoin (USD)_diff']=data['Bitcoin (USD)']-data['Bitcoin (USD)'].shift(1)

result = seasonal_decompose(data['Bitcoin (USD)'], model='additive', period=12)
data['Bitcoin (USD)_sea_diff']=result.resid

data['Bitcoin (USD)_log'] = np.log(data['Bitcoin (USD)'])
data['Bitcoin (USD)_log_diff']=data['Bitcoin (USD)_log']-data['Bitcoin (USD)_log'].shift(1)

result = seasonal_decompose(data['Bitcoin (USD)_log_diff'].dropna(), model='additive', peri)
data['Bitcoin (USD)_log_seasonal_diff']=result.resid

plt.figure(figsize=(16, 16))
plt.subplot(6, 1, 1)
plt.plot(data['Bitcoin (USD)'], label='Original')
plt.legend(loc='best')
plt.title('Original Data')
plt.xlabel('Year')
plt.ylabel('No of Bitcoin (USD)')

plt.subplot(6, 1, 2)
plt.plot(data['Bitcoin (USD)_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('Year')
plt.ylabel('Differenced No of Bitcoin (USD)')

plt.subplot(6, 1, 3)
plt.plot(data['Bitcoin (USD)_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('Year')
plt.ylabel('Seasonally djusted No of Bitcoin (USD)')

plt.subplot(6, 1, 4)
plt.plot(data['Bitcoin (USD)_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Year')
plt.ylabel('Log(No of Bitcoin (USD))')

plt.subplot(6, 1, 5)
plt.plot(data['Bitcoin (USD)_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Year')
plt.ylabel('RDiff(Log(No of Bitcoin (USD)))')
plt.subplot(6, 1, 6)

plt.plot(data['Bitcoin (USD)_log_seasonal_diff'], label='Log Transformation and regular Diff')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing and Seasonal Differencing')
plt.xlabel('Year')
plt.ylabel('SDiff(RDiff(Log(No of Bitcoin (USD))))')
plt.tight_layout()
plt.show()
data.plot(kind='line')
```

### OUTPUT:

Unprocessed Data:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/31e45aea-8b94-42c5-90a4-b4a3539a3f39" />

After regular differencing:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/b92c6adf-d581-46a8-8aa6-74f621c921f4" />

After seasonal adjustment:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/a45ec33b-6a47-40f6-95d6-4761b1e32296" />

After log transformation:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/239f823d-81dc-49e8-b4c6-408943dfa9da" />

After log transformation and regular differencing:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/db3a386a-4a83-4670-9b3f-054589da91e6" />

After log transformation, regular differencing and seasonal differencing:

<img width="1588" height="1590" alt="image" src="https://github.com/user-attachments/assets/6d82821b-00f1-4721-9451-39767e11f664" />

Overall view:

<img width="578" height="432" alt="image" src="https://github.com/user-attachments/assets/5d85f4d1-f36e-4496-b177-12cef4df0e06" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
