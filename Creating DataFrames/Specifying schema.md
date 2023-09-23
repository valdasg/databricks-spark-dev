1. As string
```python
users_schema = '''
	id INT,
	first_name STRING,
	is_customer BOOLEAN,
	amount FLOAT
	'''
users_df = spark.createDataFrame(users, schema = user_schema)

users_df.printSchema()
users_df.columns
users_df.dtypes

```
2. As list of columns, specifying just column names, schema implied from data
```python
users_schema = [
				'id',
				'first_name',
				'is_customer',
				'amount'
]
users_df = spark.createDataFrame(users, schema = user_schema)

```
1. As a Spark Types, StructType takes a list of StructFields
```python
from pyspark.sql.types import StringType, BooleanType, FloatType, IntegerType, StructType, StructField

users_schema = StrucType ([
					 StructField('id', IntegerType()),
					 StructField('first_name', StringType()),
					 StructField('is_customer', BooleanType()),
					 StructField('amoun', FloatType())
					 
])
users_df = spark.createDataFrame(users, schema = user_schema)

```