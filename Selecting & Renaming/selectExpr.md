Used as a SQL style expression.
```python
users_df.selectExpr('*').show()
users_df.alias('u').selectExpr('u.*').show()
users_df.selectExpr('id', 'first_name').show()
users_df.selectExpr(['id', 'first_name']).show()

users_df \
	.selectExpr('id', 'first_name', 'last_name', "concat(first_name, ', ', last_name) AS full_name") \
	.show()

users_df.createOrReplaceTempView('users')
spark.sql('''
select id, first_name, last_name, concat(first_name, ", ", last_name) AS full_name
FROM users
''').show()
```

