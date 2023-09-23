```python
# join(dataframe, on=none, how=none) inner is default
# on: string, list or col

# pass condition as name of columns as string if column name is the same, can also use list without equality
df.join(df1, 'id', 'inner')

# pass in standard way for different column names
df.join(df1, df.id == df1.col_id, 'inner')

# pass as list for multiple conditions
df.join(df1, [df.id == df1.col_id, df.col_name == df1.col_name1], 'inner')
```
