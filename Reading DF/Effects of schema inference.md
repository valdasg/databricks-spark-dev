If data size is big, additional time will be needed.
If schema is specified, data will not be read, thus saving time.
Schema can be inferred on json, parquet, orc.
For csv, dataframe will have system generated column names and string type objects as values. If file contain headers, specify `header=True` and `inferSchema=True`, thus defining column names. If not, use `toDF`.