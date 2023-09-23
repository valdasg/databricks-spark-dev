```python
# partitionBy(*cols)
# string or list
```

```python
df \
	.withColumn('date', date_format('date', 'yyyyMMdd')) \
	.coalesce(1) \
	.write \
	.partitionBy('date') \
	.parquet('/path/')
```

```python
# partition by multiple columns
df \
	.withColumn('date', date_format('date', 'yyyyMMdd')) \
	.withColumn('month', date_format('month', 'yyyyMM')) \
	.withColumn('year', date_format('year', 'yyyy')) \
	.coalesce(1) \
	.write \
	.partitionBy('date', 'month', 'year') \
	.parquet('/path/')
```