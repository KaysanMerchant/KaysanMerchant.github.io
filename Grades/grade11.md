---
layout: home
title: Grade 11
Date: 10/03/2025
---

## The First Project

The first project for Grade 11 Technological Studies, was the Data Visualisation project. In this assignment, we had to visualise and analyse Anscombe's Quartet. Here it is:

```Python
import matplotlib.pyplot as plt
import numpy as np

x = [10,8,13,9,11,14,6,4,12,7,5]
y1 = [8.04,6.95,7.58,8.81,8.33,9.96,7.24,4.26,10.84,4.82,5.68]
y2 = [9.14,8.14,8.74,8.77,9.26,8.1,6.13,3.1,9.13,7.26,4.74]
y3 = [7.46,6.77,12.74,7.11,7.81,8.84,6.08,5.39,8.15,6.42,5.73]
x4 = [8,8,8,8,8,8,8,19,8,8,8]
y4 = [6.58,5.76,7.71,8.84,8.47,7.04,5.25,12.5,5.56,7.91,6.89]

plt.scatter(x,y1,color="green",label="Set 1")
plt.scatter(x,y2,color="red",label="Set 2")
plt.scatter(x,y3,color="blue",label="Set 3")
x_all = x*3
y_all = y1 + y2 + y3
m, b = np.polyfit(x_all, y_all, 1)
plt.plot(sorted(x_all), [m*xi + b for xi in sorted(x_all)], color="black", linestyle="--", label="Regression (all sets)")
plt.grid(True)
plt.xlabel("x")
plt.ylabel("y")
plt.title("Relation of x values to y values")
plt.legend(loc='upper right', title='Dataset',bbox_to_anchor=(1.45, 1))
plt.show()

plt.scatter(x4,y4,color="purple")
m4, b4 = np.polyfit(x4, y4, 1)
plt.plot(sorted(x4), [m4*xi + b4 for xi in sorted(x4)], color="purple", linestyle="--", label="Regression line")
plt.grid(True)
plt.xlabel("x")
plt.ylabel("y4")
plt.title("Relation of x values to y values, set 2")
plt.show()

total_x = x + x4
mean_x = np.mean(total_x)
print("Mean of x(including x4) is",mean_x)

var_x = round(np.var(x),0)
print("Variance of x is",var_x)

total_y = y1 + y2 + y3 + y4
mean_y = round(np.mean(total_y),2)
print("Mean of y is",mean_y)

var_y = round(np.var(total_y),3)
print("Variance of y is",var_y)

var_y2 = round(np.var(y2),3)
print("Variance of y2 is",var_y2)

var_y3 = round(np.var(y3),3)
print("Variance of y3 is",var_y3)

var_y4 = round(np.var(y4),3)
print("Variance of y4 is",var_y4)

y_pred_all = [m*xi + b for xi in x_all]
y_mean_all = np.mean(y_all)
ss_res_all = sum((yi - ypi)**2 for yi, ypi in zip(y_all, y_pred_all))
ss_tot_all = sum((yi - y_mean_all)**2 for yi in y_all)
r2_all = 1 - (ss_res_all/ss_tot_all)
print(f"R² for combined y1,y2,y3: {r2_all:.4f}")

y_pred_4 = [m4*xi + b4 for xi in x4]
y_mean_4 = np.mean(y4)
ss_res_4 = sum((yi - ypi)**2 for yi, ypi in zip(y4, y_pred_4))
ss_tot_4 = sum((yi - y_mean_4)**2 for yi in y4)
r2_4 = 1 - (ss_res_4/ss_tot_4)
print(f"R² for y4: {r2_4:.4f}")
```
