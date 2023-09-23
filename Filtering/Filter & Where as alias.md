```python
# you can pass conditions:
df.filter(df.column >3)
df.where(df.column >3)

df.filter(df['column'] >3)
df.where(df['column'] >3)

df.filter(col('column') >3)
df.where(col('column') >3)

# SQL style syntax can use = or ==
df.filter('column >3')
df.where('column >3')
```