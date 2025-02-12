# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary libraries.
2. Define the functions for computeCost and gradient descent.
3. Plot the graphs for cost function and profit prediction.
4. Define the predict function and print the results.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: B VIJAY KUMAR
RegisterNumber:  212222230173
*/
```
## Import Necessary Libraries
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```
## Display the Data
```
df = pd.read_csv("ex1.txt",header = None)
```
## Prediction Graph on Profit
```
plt.scatter(df[0],df[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Poplation of City (10,000s)")
plt.ylabel("Profit")
plt.title("Profit Prediction")
```
## Define the Compute cost Function
```
def computeCost(X,y,theta):
  m=len(y)
  h=X.dot(theta)
  square_err=(h-y)**2
  return 1/(2*m)*np.sum(square_err)
```
## Display the values of Function
```
df_n = df.values
m = df_n[:,0].size
X = np.append(np.ones((m,1)),df_n[:,0].reshape(m,1),axis=1)
y = df_n[:,1].reshape(m,1)
theta = np.zeros((2,1))
computeCost(X,y,theta)
```
## Define the gradient descent Function
```
def gradientDescent(X,y,theta,alpha,num_iters):
    m=len(y)
    hi=[]

    for i in range(num_iters):
        predictions = X.dot(theta)
        error = np.dot(X.transpose(),(predictions-y))
        descent = alpha * 1/m * error
        theta -= descent
        hi.append(computeCost(X,y,theta))

    return theta,hi
```
## h(x)
```
theta, hi = gradientDescent(X,y,theta,0.01,1500)
print("hx = ", str(round(theta[0,0],2)),'+',str(round(theta[1,0],2)),'x1')
```
## Plot the cost function and Profit Prediction Graph
```
plt.plot(hi)
plt.xlabel('Iterations')
plt.ylabel('Theta')
plt.title('Cost function using Gradient Descent')

plt.scatter(df[0],df[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")
```
## Prediction function
```
def predict(x,theta):
  predictions = np.dot(theta.transpose(),x)
  return predictions[0]
```
## Prediction 1
```
predict1 = predict(np.array([1,3.5]),theta)*10000
print("Profit for Population of 35k $",str(round(predict1,0)))
```
## Prediction 2
```
predict2 = predict(np.array([1,7]),theta)*10000
print("Profit for Population of 70k $",str(round(predict2,0)))
```
## Output:

<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/59ca8c96-f3f0-492f-90dc-ebb4c05de3f2" width=500 height=400><br>
<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/0285b02c-24b8-464e-bc8e-9dd1abaa12ae" width=500 height=400><br>
<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/89f746b6-6a28-48e4-9582-51453d82e820" width=500 height=400><br>
<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/cd7c0bfd-ba02-48da-bace-615c5d74223d" width=500 height=400><br>
<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/c1f63e5d-393f-49a0-9522-250d9d28af44" width=500 height=400><br>
<img src="https://github.com/VIJAYKUMAR22007124/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119657657/ba1d4d22-bccf-4a0b-9068-126e09f75e91" width=500 height=400><br>


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
