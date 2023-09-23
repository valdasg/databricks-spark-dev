Convert literal to column type, does not work for strings
```python

# add 25 using SQL
users_df.createOrReplaceTempView('users')
spark.sql('''
	SELECT id, (amount_paid + 25) AS paid_amount
	FROM users
''') \
	.show()

# add 25 using selectExpr
users_df \
	.selectExpr('id', '(amount_paid + 25) AS paid_amount') \
	.show()

# using select
from pyspark.sql.functions import lit, col
users_df \
	.select('id', (col('amount_paid) + lit(25)).alias('amount_paid') \
	.show()
```