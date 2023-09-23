```python
from pyspark.sql.function import coalesce, lit
# takes *col and returns first non null value, note empty string is not null, to vonvert it to null cast('int')

df \
	.withColumn(coalesce('column'), lit(0)) \
	.show
```

```python
# use df.na to deal with multiple nulls

#df.fill is alias for df.fillna()
df.fill(value, subset=subset)

# note, one function applies to one data type column if you want to apply to many, chain fillna.

df.fillna(0.0, 'salary').fillna('na', 'last_name')
```