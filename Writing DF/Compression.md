```python
# default compression can be set, applicable for session
spark.sql.parquet.compression.codec
# check
spark.conf.get('spark.sql.parquet.compression.codec')

#set
spark.conf.set('spark.sql.parquet.compression.codec', 'none')

# if you do not want to compress:
compression='none'
```