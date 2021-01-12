# Different Classification Metrics with Code Example

**Confusino Matrix** with a given simple example

|     | dog | cat |
| --- | --- | --- |
| dog | 5 | 2 |
| cat | 3 | 3 |

|     | dog | cat |
| --- | --- | --- |
| dog | TP | FP |
| cat | FN | TN |


* **accuracy = (TP+TN)/(TP+TN+FP+FN)**

  ```py
  >>> from sklearn.metrics import accuracy_score
  >>> y_pred = [0, 2, 1, 3]
  >>> y_true = [0, 1, 2, 3]
  >>> accuracy_score(y_true, y_pred)
  0.5
  ```

* **precision = TP/(TP+FP)**

  ```py
  >>> from sklearn.metrics import precision_score
  >>> y_true = [0, 1, 2, 0, 1, 2]
  >>> y_pred = [0, 2, 1, 0, 0, 1]
  >>> precision_score(y_true, y_pred, average='macro')
  0.22

  ```

* **recall = TP/(TP+FN)**

  ```py
  >>> from sklearn.metrics import recall_score
  >>> y_true = [0, 1, 2, 0, 1, 2]
  >>> y_pred = [0, 2, 1, 0, 0, 1]
  >>> recall_score(y_true, y_pred, average='macro')
  0.33...

  ```

* **f1 = 2TP/(2TP+FP+FN)**

  ```py
  >>> from sklearn.metrics import f1_score
  >>> y_true = [0, 1, 2, 0, 1, 2]
  >>> y_pred = [0, 2, 1, 0, 0, 1]
  >>> f1_score(y_true, y_pred, average='macro')
  0.26...
  >>> f1_score(y_true, y_pred, average='micro')
  0.33...
  >>> f1_score(y_true, y_pred, average='weighted')
  0.26...
  >>> f1_score(y_true, y_pred, average=None)
  array([0.8, 0. , 0. ])

  ```

* **mcc = (TPxTN-FPxFN)/(sqrt(TP+FP)(TP+FN)(TN+FP)(TN+FN))**

  ```py
  >>> from sklearn.metrics import matthews_corrcoef
  >>> y_true = [+1, +1, +1, -1]
  >>> y_pred = [+1, -1, +1, +1]
  >>> matthews_corrcoef(y_true, y_pred)
  -0.33...
  ```
* **confusion matrix**

  ```py
  >>> from sklearn.metrics import confusion_matrix
  >>> y_true = [2, 0, 2, 2, 0, 1]
  >>> y_pred = [0, 0, 2, 2, 0, 2]
  >>> confusion_matrix(y_true, y_pred)
  array([[2, 0, 0],
         [0, 0, 1],
         [1, 0, 2]])

  ```
