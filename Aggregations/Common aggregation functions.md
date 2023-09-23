```python
# column objects or strings or even '*'
sum()
count()
min()
max()
avg()
stdev()
```
```python
# group key aggregation
df.groupBy('column1').agg(count('*')).show()

# total aggregation
df.select(count('*')).show())
```
```python
df \
	.filter('column1 = 2') \
	.select(sum('subtotal_of_colum1') \
	.alias('subtotals')) \
	.show()

# more complex
df \
	.filter('column1 = 2') \
	.select(
		sum('subtotal_of_colum1').alias('subtotals'),
		count('count_of_colum1').alias('subtotals')
		) \
	.show()
```

```python
# two ways to perform count
df.count() # action
df.select(count('*')) # reqires action to execute, ex show()
```