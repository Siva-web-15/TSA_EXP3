# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Date: 09.03.2026
## NAME : SIVABALAN M

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
# Import necessary packages
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv('/Gold Price (2013-2023).csv')

# Convert price column to numeric
df['Price'] = df['Price'].str.replace(',', '').astype(float)

# Create time variable
time = np.arange(len(df))
price = df['Price'].values

# ---------------------------
# Mean and Variance
# ---------------------------

mean_price = np.mean(price)
variance_price = np.var(price)

print("Mean of Price:", mean_price)
print("Variance of Price:", variance_price)

# ---------------------------
# Normalization (Z-score)
# ---------------------------

normalized_price = (price - mean_price) / np.std(price)

# ---------------------------
# Correlation Implementation
# ---------------------------

mean_time = np.mean(time)
mean_price = np.mean(price)

numerator = np.sum((time - mean_time) * (price - mean_price))
denominator = np.sqrt(np.sum((time - mean_time)**2) * np.sum((price - mean_price)**2))

correlation = numerator / denominator

print("Correlation between Time and Gold Price:", correlation)

# ---------------------------
# Store results in array
# ---------------------------

results = np.array([mean_price, variance_price, correlation])

print("Stored Results Array:", results)

# ---------------------------
# Graphical Representation
# ---------------------------

plt.figure(figsize=(10,5))
plt.plot(price, label="Original Price")
plt.plot(normalized_price, label="Normalized Price")
plt.title("Gold Price Normalization")
plt.legend()
plt.show()

# Correlation Scatter Plot
plt.figure(figsize=(8,5))
plt.scatter(time, price)
plt.title("Correlation between Time and Gold Price")
plt.xlabel("Time Index")
plt.ylabel("Gold Price")
plt.show()

```

### OUTPUT:

<img width="1168" height="725" alt="image" src="https://github.com/user-attachments/assets/a1cece5a-b5e6-417d-bfb7-77eb2acad30a" />


<img width="980" height="666" alt="image" src="https://github.com/user-attachments/assets/94b76c4f-6aa0-47df-b4e7-264a806379da" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
