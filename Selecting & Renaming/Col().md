

```python
# if there are no transformations for column string can be used, if transformation or function is needed use col().
from pyspark.sql.functions import col

col('id')
>>> Column<'id'>

user_id = col('id')

users_df \
	.select(user_id) \
	.show()

# you can nonly use functions on column type objects and not on strings. Functions return column type objects.
from pyspark.sql.functions import date_format

users_df \
	.select(col('id'), date_format('customer_from', yyyyMMdd).cast('int')) \
	.alias('customer_from') \
	.show()

cols = [col('id'), date_format('customer_from', yyyyMMdd).cast('int').alias('customer_from')]

users_df \
	.select(*cols) \
	.show()
```