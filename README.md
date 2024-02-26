# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date:
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION
```
import numpy as np
from tabulate import tabulate
x = list(map(int, input("Enter a list of years").split()))
y = list(map(int, input("Enter a list of observation").split()))

X = [i - x[len(x)//2] for i in x]
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]

table = [[i, j, k, l, m] for i, j, k, l, m in zip(x, y, X, x2, xy)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2014", "X^2", "xy"], tablefmt="grid"))


n=len(x)
b=(n*sum(xy)-sum(y)*sum(X))/(n*sum(x2)-(sum(X)*2))
a=(sum(y)-b*sum(X))/n
print(a,b)
l=[]
for i in range(n):
  l.append(a+b*X[i])
print(l)
l=[]
for i in range(n):
  l.append(a+b*X[i])
import matplotlib.pyplot as plt
plt.xlabel("Years")
plt.ylabel("Production")
plt.plot(x,l)
```
B- POLYNOMIAL TREND ESTIMATION
```

import numpy as np
from tabulate import tabulate
# x = list(map(int, input("Enter a list of years").split()))
# y = list(map(int, input("Enter a list of observation").split()))
x = [2011,2012,2013,2014,2015,2016]
y = [100,107,128,140,181,192]
X = [2*(i-(sum(x)/len(x))) for i in x]
print(X)
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]
x3 = [i ** 3 for i in X]
x4 = [i ** 4 for i in X]
x2y=[i*j for i,j in zip(x2,y)]

table = [[i, j, k, l, m,n,o,p] for i, j, k, l, m,n,o,p in zip(x, y, X, x2, x3,x4,xy,x2y)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2013", "X^2", "X^3","X^4","xy","x2y"], tablefmt="grid"))
coeff=[[len(X),sum(X)],[sum(X),sum(x2)]]

coeff=[[len(x),sum(X),sum(x2)],[sum(X),sum(x2),sum(x3)],[sum(x2),sum(x3),sum(x4)]]
Y=[sum(y),sum(xy),sum(x2y)]
A=np.array(coeff)
B=np.array(Y)
try:
  solution=np.linalg.solve(A,B)
  # print(solution)
except:
  print("error")
a,b,c=solution
# print(a,b,c)
print("Polynomial trend equation y=%.2f+%0.2fx+%.2fx^2"%(a,b,c))
```
### OUTPUT
A - LINEAR TREND ESTIMATION

![Screenshot 2024-02-26 220645](https://github.com/Vishwarathinam/TSA_EXP2/assets/95266350/921538f5-635b-4b63-aaf1-d69128a3e63f)

![Screenshot 2024-02-26 220654](https://github.com/Vishwarathinam/TSA_EXP2/assets/95266350/5717d2b9-9e1d-4fe1-84c6-c496f42a8f27)

B- POLYNOMIAL TREND ESTIMATION

![Screenshot 2024-02-26 220813](https://github.com/Vishwarathinam/TSA_EXP2/assets/95266350/03ba749f-d66c-44fb-affe-83c81bec5f12)

![4](https://github.com/Vishwarathinam/TSA_EXP2/assets/95266350/43d55b39-3064-469a-8d7d-b65b70e4468a)

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
