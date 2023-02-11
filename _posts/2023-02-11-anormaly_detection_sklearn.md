---
layout: post
title: anormaly detection
category: algorithm
tag: code
---

### Anormaly detection 
- type 1: outlier detection, semi-supervised (outliers are inside the data)
- type 2: novelty detection, unsupervided (outliers are from new data)

#### 1. methods in sklearn
##### 1) Isolation Forest 
- 1) randomly select a feature to classify data into two sets
- 2) calculate a grade for each data point (lower the grade, higher possibility to be an outlier)

---
layout: post
title: 1st article
category: test
tag: codes
---


```python
from sklearn.ensemble import IsolationForest

X = [[-1.1], [0.3], [0.5], [100]]
n_estimators = 10        # number of learners
max_samples = len(X)     # max number of samples in a cluster
max_features = 1         # max number of features

clf = IsolationForest(random_state=0, n_estimators=n_estimators, max_samples=max_samples, max_features=max_features).fit(X)
clf.predict(X)   # 1: norma;, -1: abnormal
```




    array([ 1,  1,  1, -1])



##### 2) Local Outlier Factor
- assess the variance with neighbors, if exceed certain thres, then it is abnormalty
- 1) calculate the local density (points with higher local density is less likely to be an outlier)
- 2) calculate the LOF=density(this point)/density(neighbor points)


```python
from sklearn.neighbors import LocalOutlierFactor

clf = LocalOutlierFactor(n_neighbors=2)
clf.fit_predict(X)   # 1: norma;, -1: abnormal
```




    array([ 1,  1,  1, -1])



##### 3) OneClassSVM !Very sensitive to outliers !Can be slow (use SGDOneClassSVM)
- if external points is similar to most internal points, then it is "normal", else, "abnormal" 
- Similarly like SVM, it is to find a superplane to max the distance btw internal and the boundary


```python
from sklearn.svm import OneClassSVM

clf = OneClassSVM(gamma='auto').fit(X)
# 异常/离群值返回 -1，离群值返回 +1
clf.predict(X)
```




    array([-1,  1, -1,  1])



##### 4) Elliptic Envelop
- Assume Gaussian distribution, find an elliptic to classify internal points and outliers


```python
import numpy as np
from sklearn.covariance import EllipticEnvelope

cov = EllipticEnvelope(random_state=0).fit(X)
cov.predict(X)
```




    array([ 1,  1,  1, -1])




```python
nbconver --to markdown anormaly_detection_sklearn.ipynb
```


      File "/tmp/ipykernel_3294764/3164443436.py", line 1
        nbconver --to markdown anormaly_detection_sklearn.ipynb
                      ^
    SyntaxError: invalid syntax




```python

```
