```python
# groupBy(*col)
# takes list, string or col()

df.groupBy('column').agg({'column1': 'mean'})
df.groupBy('column').avg()
df.groupBy(['column1', 'column2']).count()

# groupBy returns groupby grouped dataframe which need to be aggregated by aggregarion functions first

# if column not passed, will try to perform aggregations on all numeric functions

df.groupBy().count().show()
```

```python
# using direct functions (sum, min, max...). You can only pass one aggregation function.
df \
	.groupBy('id') \
	.sum('quantity', 'subtotal') \
	.show()
# sum takes string as argument, you can not pass functions as round, you need to rename columns using toDF or withColumnRenamed and then do withColumn and then pass round

df \
	.groupBy('id') \
	.sum('quantity', 'subtotal') \
	.toDF('id', 'quantity', 'subtotal') \
	.withColumn('subtotal', round('subtotal', 2)) \
	.show()
```

```python
# group aggregations using agg, you can also use functions inside of agg, like round

# create grouped df
df_grouped = df.groupBy('id')

# agg(*exprs), exprs = dict or list of col objects
df_grouped.agg({'*': 'count'})
# or
df_grouped.agg(sum(col('quantity'), round(avg(col('price')),2)) 

```

```python
# if you pass dict to agg you can not use functions inside aggregations thus:
df_grouped \
	.agg({'column1': 'sum', 'column2': 'avg'}) \
	.toDF('sum', 'average') \
	.withColumn('average', round('average', 2)) \
	.show()
```

```python
# you can not pass different functions to same column, since dict keysshould be unique ----> this will not work
df_grouped \
	.agg({'column1': 'sum', 'column1': 'avg'}) \
	.show()
# use colum objects instead
df_grouped \
	.agg(
		sum('column1').alias('sum')),
		round(avg('column1'), 2).alias('average') \
	.show()
```