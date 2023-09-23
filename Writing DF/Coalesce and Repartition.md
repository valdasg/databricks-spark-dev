```python
# coalesce not to be confused with function to pick up first value after null

# coealesce() takes number of partitions, does not reshuffle data, only to reduce partitions

# repartition() takes colum name and partitions number, incurs shuffling
```

```python
# get number of partitions
df.rdd.getNumPartitions()

df.coalesce(num)
df.repartition(num, 'col1', 'col2')

```