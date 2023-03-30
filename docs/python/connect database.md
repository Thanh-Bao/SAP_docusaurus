```python

import pyodbc
import pandas as pd
dbcn = pyodbc.connect('DRIVER={SQL Server};SERVER=tuan.baobaostore.com,5002;DATABASE=bonsaidb;UID=SA;PWD=g3hn94y954fc93@AVBVR54')

# lesson 10
dataframe = pd.read_sql("SELECT * FROM user", dbcn)
print(dataframe)
```
