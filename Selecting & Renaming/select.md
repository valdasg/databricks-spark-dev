```python
users_df.select('*').show()
users_df.select('id', 'first_name').show()
users_df.select(['id', 'first_name']).show()
users_df.alias('u').select('u.*').show()

from pyspark.sql.functions import col, lit, concat
users_df.select(col('id'), 'first_name')

users_df \
	.select(col('id'), 'first_name', 'second_name') \
	.concat(col('first_name'), lit(', '), col('second_name')).alias('full_name') \
	.show()
```