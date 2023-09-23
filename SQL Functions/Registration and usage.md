```python
# develop logic with python
# register function with `spark.udf.register` and asign it to variable
# variable can be used as a part od dataframe APIs, like select, filter, etc
# register(name, function, returnType=None)
# use spark.udf.register for SQL queries, udf() for python
```

```python
dc = spark.udf.register('date_convert', lambda d: int(d[:10].replace('-', ' ')))

df.select(dc('date').alias('fixed_date
df.filter(dc('date') == 20230421)
```

```python
# Spark SQL queries
df.selectExpr('date_convert('date) AS fixed_date')

df.createOrReplaceTempView('orders')
spark.sql('''
SELECT o.*, date_convert(date) AS fixed_date
FROM orders AS o
''').show()



df.createOrReplaceTempView('orders')
spark.sql('''
SELECT o.*, date_convert(date) AS fixed_date, count(*)
FROM orders AS o
WHERE date_convert('date') = 20230101
GROUP BY 1
''').show()

```

```python
def data_clean(c):
	return c.strip() if c.strip() != '\\N' else None

data_clean = spark.udf.register('data_clean', data clean)
 ```