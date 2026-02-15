# Data Cleaning 

## Table of Contents
- [Introduction](#introduction)
- [Handling Missing Data](#handling-missing-data)
- [Filling in Missing Data](#filling-in-missing-data)
- [Removing Duplicates](#removing-duplicates)
- [Transforming Data Using a Function or Mapping](#transforming-data-using-a-function-or-mapping)
- [Replacing Values](#replacing-values)
- [Renaming Axis Indexes](#renaming-axis-indexes)
- [Conclusion](#conclusion)

### Introduction
This file will define and justify of each and every process in data analytics: data cleaning. 

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

### Removing Duplicates
```Python
data = pd.DataFrame({'k1': ['one', 'two'] * 3 + ['two'],
                    'k2': [1,1,2,3,3,4,4]})
data
data.duplicated()
data.drop_duplicates()
data['v1'] = range(7)
data.drop_duplicates(['k1'])
data.drop_duplicates(['k1', 'k2'], keep='last')
data = pd.DataFrame({'food': ['bacon', 'pulled pork', 'bacon',
                             'Pastrami', 'corned beef', 'Bacon',
                            'pastrami', 'honey ham', 'nova lox'],
                    'ounces': [4, 3, 12, 6, 7.5, 8, 3, 5, 6]})
data
```

### Transforming Data Using a Function or Mapping
```Python
meat_to_animal = {
    'bacon': 'pig',
    'pulled pork': 'pig',
    'pastrami': 'cow',
    'corned beef': 'cow',
    'honey ham': 'pig',
    'nova lox': 'salmon'
}
lowercased = data['food'].str.lower()
lowercased
data['animal'] = lowercased.map(meat_to_animal)data.rename(index=str.title, columns=str.upper)
data
data['food'].map(lambda x: meat_to_animal[x.lower()])
```

### Replacing Values
```Python
import pandas as pd
data = pd.Series([1., -999., 2., -999., 3.])
data
import numpy as np
data.replace(-999, np.nan)
data.replace([-999, -1000], np.nan)
data.replace([-999, -1000], [np.nan, 0])
```

### Renaming Axis Indexes
```Python
data = pd.DataFrame(np.arange(12).reshape((3,4)),
                   index = ['Ohio', 'Colorado', 'New York'],
                   columns = ['one', 'two', 'three', 'four'])
print(data)
transform = lambda x: x[:4].upper()
data.index.map(transform)
data.rename(index=str.title, columns=str.upper)
data.rename(index={'OHIO':"INDIANA"},
           columns = {'three':'peekaboo'})
data.rename(index={'OHIO': 'INDIANA'}, inplace=True)
data
```

### Conclusion
This file consist of Handling Missing Data, Filling in Missing Data, Removing Duplicates, Transforming Data Using a Function or Mapping, Replacing Values, Renaming Axis Indexes.
