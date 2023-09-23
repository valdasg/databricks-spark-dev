Narrow transformation do not cause shuffle of partitions:
```python
df.select
df.filter
df.withColumn
df.withColumnRenamed
```
Any function that causes reshuffle is wide transformation:
```python
df.distinct
df.union
df.join
df.groupBy
df.sort
df.orderBy
```
