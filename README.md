# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm

Step 1: 
Import the NumPy and sys libraries.

Step 2: 
Get the number of unknowns and read the augmented matrix.

Step 3:
Apply Gaussian Elimination to convert the matrix into upper triangular form.

Step 4: 
Apply back substitution to find and display the solution values of the variables.

## Program:
```python
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: Aman Nair
RegisterNumber: 212225240008
'''

import os 
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import sys

#Reading number of unknowns 
n=int(input())

# Making numpy array of nxn+1 size and initializing to zero for storing augmented matrix
a=np.zeros((n,n+1))

# Making numpy array of n size and initializing to zero for storing solution vector
x=np.zeros(n)

# reading augmented matrix coefficients
for i in range(n):
    for j in range(n+1):
        a[i][j]=float(input())
        
# Applying Gauss elimination 
for i in range(n):
    if(a[i][i]==0.0):
        sys.exit("Divide by zero detected!")
    for j in range(i+1,n):
        ratio=a[j][i]/a[i][i]
        for k in range(n+1):
            a[j][k]=a[j][k]-ratio*a[i][k]
            
#Back Substitution
x[n-1]=a[n-1][n]/a[n-1][n-1]
for i in range(n-2,-1,-1):
    x[i]=a[i][n]
    for j in range(i+1,n):
        x[i]=x[i]-a[i][j]*x[j]
    x[i]=x[i]/a[i][i]
    
#Displaying Solution
for i in range(n):
    print("X%d = %0.2f "%(i,x[i]),end='')

```

## Output:

<img width="1022" height="683" alt="image" src="https://github.com/user-attachments/assets/696661c8-fb7b-4f82-9d91-30717c590393" />


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

