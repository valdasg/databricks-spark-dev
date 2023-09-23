
```python
# function on Data Frame, can pass string or column
# if column does not exist noerror is thrown
df.drop('column')
# or
df.drop(col('column'))
# or
df.drop(df['column'])

# dropping multiple colums, only accept strings, not col
df.drop('column1', 'colun2')

# you can not pass list to drop, need to use *e
columns = ['column1', 'column2']
df.drop(*columns)
```

```python
# dropping duplicates
# distinct(), drop_duplicates() or alias dropDuplicates()

# distinct is a dataframe  function, takes no arguments
df.distinct()

# dropDuplicates() takes one argument which is subset of columns as list, even if list contains one item
df.dropDuplicates(['column1', 'column2'])
```

```python
# drop null values
# use df.na.drop or alias df.dropna
# supports thresh argument, drops less than thresh value
# support how argument (any or all)
# support subset (list of columns)
# thresh overwrites how!!!

df.drop('any')
df.drop(thresh=2)
df.drop(how ='all', thresh = 2, subset = ['column1', 'column2'])
```