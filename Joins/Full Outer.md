```python
# specify full, full_outer, fullouter
df \
	.join(df1, 'users', 'full')
```
```python
# full is used to get missing data often, for this purpose use coalesce()

df.alias('a') \
	.join(df1.alias('b'), 'email', 'full') \
	.select(
		coalesce('a.email', 'b.email').alias('email'),
		coalesce('a.name', 'b.name').alias('name')
		)
```