
```python
#inner join, can skip standard inner. If column name is the same, use string, it will return only one same colums
df \
	.join(df1, df.id = df1.id)
#or
df \
	.join(df1, 'id')
```

```python
#to resolve ambigiuos column names mention df, if name is the same, you can skip it
df.alias('a') \
	.join(df1.alias('b'), a.id == b.id) \
	.groupBy(a['id']) \
	.count()
```