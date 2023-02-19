---
layout: post
title: data quality
category: algorithm
tag: python package
---

## Deepchecks [validation machine learning models and data]
- Project source:https://github.com/deepchecks/deepchecks] 
- Coverage of data: tabular, Computer Vision data, text data (to come)
- Level of check results: fail, pass, warning, error
- 1) Data Integrity check: check the data quality issues 
- 2) Train Test Validation check: check the suitability for training and testing data setting 
- 3) Model Evaluation check: test the model performance against model selection, data portion results btw train and test
- other resources: https://zhuanlan.zhihu.com/p/526387718

### 1. Tabular Data 
#### 1-1. Data Integrity Check


```python
from deepchecks.tabular import datasets
from deepchecks.tabular import Dataset
from deepchecks.tabular.suites import data_integrity

import pandas as pd

def add_dirty_data(df):
    # change strings
    df.loc[df[df['type'] == 'organic'].sample(frac=0.18).index,'type'] = 'Organic'
    df.loc[df[df['type'] == 'organic'].sample(frac=0.01).index,'type'] = 'ORGANIC'
    # add duplicates
    df = pd.concat([df, df.sample(frac=0.156)], axis=0, ignore_index=True)
    # add column with single value
    df['Is Ripe'] = True
    return df


# 1-1. load data
data = datasets.regression.avocado.load_data(data_format='DataFrame', as_train_test=False)
# 1-2. add noise
dirty_df = add_dirty_data(data)
# 1-3.create deepchecks dataset, includes metadata (label, date, index, etc.)
ds = Dataset(dirty_df, cat_features= ['type'], datetime_name='Date', label= 'AveragePrice')

# 2-1. run Suite
integ_suite = data_integrity()        # call a test func
suite_result = integ_suite.run(ds)
# Note: the result can be saved as html using suite_result.save_as_html()or exported to json using suite_result.to_json()

# 3-1. result show
suite_result.show()
# 3-2. result save
# suite_result.save_as_html(), suite_result.to_json()
```



#### 1-2. Train-Test Validation Suite
- Usage: compare two data subsets


```python
from deepchecks.tabular.datasets.classification import lending_club
from deepchecks.tabular import Dataset
from deepchecks.tabular.suites import train_test_validation
import pandas as pd

# 1-1. load data
data = lending_club.load_data(data_format='Dataframe', as_train_test=False)

# 1-2. transform data: conert date column to datetime, `issue_d`` is date column
data['issue_d'] = pd.to_datetime(data['issue_d'])

categorical_features = ['addr_state', 'application_type', 'home_ownership', 'initial_list_status', 'purpose', 'term', 'verification_status', 'sub_grade']
index_name = 'id'
label = 'loan_status' # 0 is DEFAULT, 1 is OK
datetime_name = 'issue_d'
columns_metadata = {'cat_features' : categorical_features, 'index_name': index_name,
                    'label':label, 'datetime_name':datetime_name}

# 1-3. train-test split: use data from June and July for train and August for test:
train_df = data[data['issue_d'].dt.month.isin([6, 7])]
test_df = data[data['issue_d'].dt.month.isin([8])]

train_ds = Dataset(train_df, label=label,cat_features=categorical_features, index_name=index_name, datetime_name=datetime_name)
test_ds = Dataset(test_df, label=label,cat_features=categorical_features, index_name=index_name, datetime_name=datetime_name)

# 2-1. define model
validation_suite = train_test_validation()
suite_result = validation_suite.run(train_ds, test_ds)
# Note: the result can be saved as html using suite_result.save_as_html()
# or exported to json using suite_result.to_json()
suite_result
```


#### 1-3. Model Evaluation Suite
- evaluate model performance 
- 1) Thorough analysis of the model’s performance before deploying it.
- 2) Evaluation of a proposed model during the model selection and optimization stage.
- 3) Checking the model’s performance on a new batch of data (with or without comparison to previous data batches).


```python
from deepchecks.tabular.datasets.regression import wine_quality
from sklearn.model_selection import train_test_split
from sklearn.ensemble import GradientBoostingRegressor
from deepchecks.tabular import Dataset
from deepchecks.tabular.suites import model_evaluation

# 1. load data
data = wine_quality.load_data(data_format='Dataframe', as_train_test=False)

# 2. define model, and train
X_train, X_test, y_train, y_test = train_test_split(data.iloc[:, :-1], data['quality'], test_size=0.2, random_state=42)
gbr = GradientBoostingRegressor()
gbr.fit(X_train, y_train)


# 3. evaluate model performance
train_ds = Dataset(X_train, label=y_train, cat_features=[])
test_ds = Dataset(X_test, label=y_test, cat_features=[])

evaluation_suite = model_evaluation()
suite_result = evaluation_suite.run(train_ds, test_ds, gbr)
# Note: the result can be saved as html using suite_result.save_as_html()
# or exported to json using suite_result.to_json()
suite_result.show()
```


