```python
# you can read in two ways:
# read.csv and format + load
# uses option or options
# suppurted formats: csv, text, json, parquet, orc,
# xml, avro nned vendor specific plugins

# steps reading file:
# check if file exists in location: hdfs dfs -ls
# check file format
# check delimiters
# check headers
# check compression

spark.read.text('/path/').show()
spark.read.json('/path/').show()
spark.read.parquet('/path/').show()
```

