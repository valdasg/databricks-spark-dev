```python
# same as csv

```python
# pass schema
schema = '''
name string,
surname string,
id int
'''

schema_struct = StructType([
	StructField('name', StringType()),
	StructField('suname', StringType()),
	StructField('suname', IntegerType())
	]
)


spark \
	.read \
	.schema(schema) \
	.json('/path/')
# or
spark \
	.read \
	.json('/path/', schema = schema_struct)

```

```python
# for parquet, sometimes you get errors with integer and timestamp in schemas. Change it to LongType and String and cast if needed.
```