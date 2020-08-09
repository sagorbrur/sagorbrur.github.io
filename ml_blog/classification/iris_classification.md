
# IRIS Data Classification
We will do the following steps to classfy iris data:

* load iris data
* create feature
* build model and fit data
* predict

## Requiremetns
  - pandas
  - numpy
  - sklearn

## Loading IRIS dataset

```py
import pandas as pd

df = pd.read_csv('iris.csv')

print(df.head())
print(df.describe())

```

## Create Feature from Loaded Data

```py
import numpy as np
X = []
y = []


for sl, sw, pl, pw in zip(df['sepal length'], df['sepal width'], df['petal length'], df['petal width']):
    x = [sl, sw, pl, pw]
    X.append(x)


for label in df['species']:
    if label =='se' or label == 'setosa':
        y.append(0)
    elif label=='versicolor':
        y.append(1)
    else:
        y.append(2)

X = np.array(X)
y = np.array(y)
```

## Build Model and Fit Data

```py
from sklearn.svm import SVC
model = SVC()
model.fit(X, y)

```
It's done training. Let predict

## Predict

```py
model.predict([[1, 2, 3, 4]])

```
