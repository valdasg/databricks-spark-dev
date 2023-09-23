```python
spark \
	.read \
	.csv('/path/') \
	.write \
	.partitionBy('Year') \
	.csv('/path/')
```

```python
# to take advantage of pruning it dataframe should be partitioned.

# pruning effect, no prunning happen
spark \
	.read \
	.csv('/path/Year = 2023')

# pruning runs automatically
spark \
	.read \
	.csv('/path/') \
	.filter('Year = 2023') \

# pruning using sql
df.createOrReplaceTempView('df_sql')
spark.sql('''
SELECT count(*)
FROM df_sql
WHERE YEAR = 2004
''').show()
```