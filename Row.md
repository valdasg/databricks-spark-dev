Row is an element of which dataframes are constructed.
```python
users = [('Tom', 20), ('John', 43), ('Timothy', 32)]
spark.createDataFrame(ages)

# to convert dataframe into list of rows do
df.collect()

from pyspark.sql import row
# rows constructed by adding *args or *kwargs

# with *args
r = row('Alice', 20)

# or with *kwargs
r = row(user = 'Alice', age = 20)

# when using *kwargs you can access elelemnts of row with key
r.user
# or
r['user']

```

