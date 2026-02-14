# Data Cleaning 

## Table of Contents
- [Introduction](#introduction)
- [Handling Missing Data](#handling-missing-data)
- [Filling in Missing Data](#filling-in-missing-data)
- [Conclusion](#conclusion)

### Introduction
This file will define and justify of each and every process in data analytics. 

### Handling Missing Data 
```Python
import pandas as pd
import numpy as np
string_data = pd.Series(['aardvak', 'artichoke', np.nan, 'avocado'])
string_data
string_data.isnull()
string_data[0] = None
string_data.isnull()
from numpy import nan as NA
data = pd.Series([1, NA, 3.5, NA, 7])
data.dropna()
data[data.notnull()]
data = pd.DataFrame([[1., 6.5, 3.], [1., NA, NA],
                   [NA, NA, NA], [NA, 6.5, 3.]])
cleaned = data.dropna()
data
print(cleaned)
data.dropna(how='all')
data[4] = NA
data
data.dropna(axis=1, how='all')
df = pd.DataFrame(np.random.randn(7,3))
df.iloc[:4, 1] = NA
df.iloc[:2, 2] = NA
df
df.dropna()
df.dropna(thresh=2)
```

### Filling in Missing Data
```Python
df.fillna(0)
df.fillna({1:0.5, 2: 0})
_ = df.fillna(0, inplace=True)
df
df = pd.DataFrame(np.random.randn(6,3))
df.iloc[2:, 1] = NA
df.iloc[4:, 2] = NA
df
df.fillna(method='ffill')
df.fillna(method='ffill', limit=2)
data = pd.Series([1., NA, 3.5, NA, 7])
data.fillna(data.mean())
```

### Conclusion
This file consist of Handling Missing Data, Filling in Missing Data.
