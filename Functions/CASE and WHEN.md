```python

df \
	.withColumn(
	'column',
	expr("""
	CASE WHEN column IS NULL OR column = '' THEN 0
	ELSE column
	END
	"""))
```

```python
from pyspark.sql.functions import when
df \
	.withColumn('column', when((col('column').isnull()) | (col('column') == lit(''), 0).othrewise(col('column'))

# chain whens if many conditions needed
```