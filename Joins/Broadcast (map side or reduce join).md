```python
# important configs
spark.conf.get('spark.sql.autoBroadcastJoinThreshold')
# default 10mb, always performed for smaller

# to disable braodcast
spark.conf.get('spark.sql.autoBroadcastJoinThreshold', '0')

# to use broadcast on larger dataframes use broadcast() function

broadcast(df).join(df1, 'id')
#or
df.join(broadcast(df1), 'id')
```