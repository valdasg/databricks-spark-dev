```python
# returns multiplied datasets, dfcount() * df1.count()
df.crossJoin(df1)
# or
df.join(df1, how = 'cross')
```