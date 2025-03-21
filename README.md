# 🌤️ Weather Data Analysis (Python, NumPy)

## 📌 Project Overview  
This project performs **weather data analysis** using **NumPy**. It generates random daily temperatures, analyzes trends, and identifies key weather patterns like **heatwaves and cold waves**.  

## 🔧 Technologies Used  
- **Python**  
- **NumPy** (for numerical computations)  

## 📊 Features & Insights  
✔ **Generates** 30 days of random temperature data (20°C to 40°C).  
✔ **Calculates Key Metrics**: Mean, Min, Max temperatures.  
✔ **Identifies Temperature Trends**:  
   - Days above/below the mean temperature.  
   - Days with the highest increase/decrease in temperature.  
✔ **Detects Extreme Weather Events**:  
   - **Heatwave Days** (Temp > 35°C)  
   - **Coldwave Days** (Temp < 25°C)  
✔ **Generates a Weather Report** summarizing findings.  

## Conclusion
-  I have identified fluctuations in daily temperature patterns.
-  The analysis helps in understanding climate trends and weather conditions.
-  Future improvements could include real-world weather data and machine learning models for temperature forecasting.

---

```python

import numpy as np
import matplotlib.pyplot as plt
temps = np.random.randint(20,41,30)
print("\nTemperature:\n", temps)

Mean_temp = np.mean(temps)
min_temp = np.min(temps)
max_temp = np.max(temps)
print("\nMean_temp :\n", Mean_temp)
print("\nmin_temp :\n", min_temp)
print("\nmax_temp:\n", max_temp)

above_mean_count = np.sum(temps > Mean_temp)
below_mean_count = np.sum(temps < Mean_temp)

print("\nDays above mean temperature:", above_mean_count)
print("\nDays below mean temperature:", below_mean_count)

equal_mean_count = np.sum(temps == Mean_temp)
print("\nDays with mean temperature:", equal_mean_count)

# Calculate daily temperature changes
temp_changes = np.diff(temps)

# Find the day with max and min temperature change
max_increase_day = np.argmax(temp_changes) + 1  # Add 1 since np.diff() reduces size by 1
max_decrease_day = np.argmin(temp_changes) + 1

print("\nDay with Maximum Temperature Increase:", max_increase_day)
print("Day with Maximum Temperature Drop:", max_decrease_day)

# Identify heatwave and coldwave days
heatwave_days = np.where(temps > 35)[0] + 1  # Days are 1-based index
coldwave_days = np.where(temps < 25)[0] + 1

print("\nHeatwave Days:", heatwave_days)
print("Coldwave Days:", coldwave_days)

print("\n Weather Analysis Report:")
print(f"- Mean Temperature: {Mean_temp:.2f}°C")
print(f"- Min Temperature: {min_temp}°C")
print(f"- Max Temperature: {max_temp}°C")
print(f"- Days Above Mean: {above_mean_count}")
print(f"- Days Below Mean: {below_mean_count}")
print(f"- Day with Max Temp Increase: {max_increase_day}")
print(f"- Day with Max Temp Drop: {max_decrease_day}")
print(f"- Heatwave Days: {heatwave_days}")
print(f"- Coldwave Days: {coldwave_days}")

# Line Plot – Daily Temperature Trends
days = np.arange(1, 31)  # Days from 1 to 30

plt.figure(figsize=(10, 5))
plt.plot(days, temps, marker='o', linestyle='-', color='b', label='Temperature')
plt.axhline(y=Mean_temp, color='r', linestyle='--', label='Mean Temperature')

plt.xlabel('Day')
plt.ylabel('Temperature (°C)')
plt.title('Daily Temperature Trends')
plt.legend()
plt.grid(True)

# Save the figure
plt.savefig("daily_temperature_trends.png", dpi=300, bbox_inches='tight')
plt.show()

# Bar Chart – Days Above & Below Mean Temperature
plt.figure(figsize=(6, 4))
plt.bar(['Above Mean', 'Below Mean'], [above_mean_count, below_mean_count], color=['green', 'red'])

plt.xlabel('Temperature Category')
plt.ylabel('Number of Days')
plt.title('Days Above & Below Mean Temperature')

# Save the figure
plt.savefig("days_above_below_mean.png", dpi=300, bbox_inches='tight')
plt.show()

# Histogram – Temperature Distribution
plt.figure(figsize=(6, 4))
plt.hist(temps, bins=6, color='purple', edgecolor='black', alpha=0.7)

plt.xlabel('Temperature (°C)')
plt.ylabel('Frequency')
plt.title('Temperature Distribution Over 30 Days')

# Save the figure
plt.savefig("temperature_distribution.png", dpi=300, bbox_inches='tight')
plt.show()
```python

## 📸 Sample Output  
```python
Temperature:
 [24 22 22 36 26 40 21 22 33 22 24 26 22 29 24 28 21 39 26 28 39 32 20 34
 37 29 33 30 26 29]

Mean_temp :
 28.133333333333333

min_temp :
 20

max_temp:
 40

Days above mean temperature: 13

Days below mean temperature: 17

Days with mean temperature: 0

Day with Maximum Temperature Increase: 17
Day with Maximum Temperature Drop: 6

Heatwave Days: [ 4  6 18 21 25]
Coldwave Days: [ 1  2  3  7  8 10 11 13 15 17 23]

 Weather Analysis Report:
- Mean Temperature: 28.13°C
- Min Temperature: 20°C
- Max Temperature: 40°C
- Days Above Mean: 13
- Days Below Mean: 17
- Day with Max Temp Increase: 17
- Day with Max Temp Drop: 6
- Heatwave Days: [ 4  6 18 21 25]
- Coldwave Days: [ 1  2  3  7  8 10 11 13 15 17 23]

## 📸 Sample Visualizations  

### 🔹 Daily Temperature Trends  
![Daily Temperature](daily_temperature_trends.png)  

### 🔹 Days Above & Below Mean Temperature  
![Above & Below Mean](days_above_below_mean.png)  

### 🔹 Temperature Distribution  
![Temperature Histogram](temperature_distribution.png)  
```python

