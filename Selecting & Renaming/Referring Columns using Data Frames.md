```python
from pyspark.sql.functions import col

# returns col object
users_df['id']

users_df \
	.select(users_df['id'], users_df['first_name']) \
	.show()

# will not work
users_df \
	.alias('u')
	.select(u['id'], u['first_name']) \
	.show()

# will work
users_df \
	.alias('u')
	.select(u.id, u.first_name) \
	.show()

# can not use use col() in selectExp as it only excepts SQL type syntax
users_df \
	.selectExpr(col('id')) \
	.show()
```