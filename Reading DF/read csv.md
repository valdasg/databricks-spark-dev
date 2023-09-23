```python
# two ways:
spark.read.csv('/path/')
# or
spark.read.format('csv').load('/path/')
```

```python
# pass schema
schema = '''
name string,
surname string,
id int
'''

spark \
	.read \
	.schema(schema) \
	.csv('/path/')
# or
spark \
	.read \
	.csv('/path/', schema = schema)
```

```python
# using toDF to infer schema
columns = ['id', 'name', 'surname']

spark \
	.read \
	.option('inferSchema', True) \
	.csv('/path/') \
	.toDF(*columns)
```

```python
# specify delimiter
spark \
	.read \
	.schema(schema) \
	.csv('/path/') \
	.sep('|')

# or
spark \
	.read \
	.csv('/path/', schema = schema, sep = '|')
```

```python
# using option / options
# use option multiple times, options as key - value
# if option is not correct it will be ignored not throwing any errors

df = spark.read \
	.csv(
		'/path/',
		sep='|',
		header=None,
		inferSchema=True
		) \
	.toDF(*columns)
# or
df = spark.read \
	.format('csv') \
	.load(
		'/path/',
		sep='|',
		header=None,
		inferSchema=True
		) \
	.toDF(*columns)

# or
df = spark.read \
	.option('sep', '|') \
	.option('header', None) \
	.option('inferschema', True)
	.csv('/path') \
	.toDF(*columns)

# or
df = spark.read \
	.options(sep = '|', header=None, inferschema=True) \
	.csv('/path') \
	.toDF(*columns)
```

```python
# or
options = {'sep': '|',
		   'header': None,
		   'inferschema': True
		}

df = spark.read \
	.options(**options) \
	.csv('/path') \
	.toDF(*columns)
```

```python
# or
df = spark.read \
	.options(**options) \
	.format('csv') \
	.load('/path/') \
	.toDF(*columns)
```