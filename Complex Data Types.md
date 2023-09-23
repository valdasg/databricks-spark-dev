**Arrays

```python
users = [ 
	{
		'id': 1,
		'name': John,
		'phone_numbers': ['+370444444444', '999999999'] 
	}
]

from pyspark.sql import Row
users_df = spark.createDataFrame([Row(**user) for user in users])
# list in dictionary is created as array data type:
# phone_numbers: array
	# element: string

from pyspark.sql.functions import explode
# explode elelments into separate columns
users_df \
	.withColumn('phone_number', explode('phone_numbers')) \
	.drop('phone_numbers') \
	.show()
# explode does not include records if column to explode is null, to include it use explode_outer()

#to access element in array, use col function
from pyspark.sql.functions import col
userrs_df \
	select ('id', col('phone_numbers')[0].alias('home'), col('phone_numbers')[1].alias('mobile')) \
	.show()

```
**Maps
```python
users = [ 
	{
		'id': 1,
		'name': John,
		'phone_numbers': {'mobile': '+370444444444',
						'home': '999999999'}
	}
]

from pyspark.sql import Row
users_df = spark.createDataFrame([Row(**user) for user in users])
# list in dictionary is created as array data type:
# phone_numbers: map
	# key: string
	# value: string

#to access element in array, use col function
from pyspark.sql.functions import col
users_df \
	select (col('phone_numbers')['mobile'])
	.show()

from pyspark.sql.functions import explode

users_df \
	.select('*', explode('phone_numbers')) \
	.withColumnRenamed('key', 'phone_type') \
	.withColumnRenamed('value', 'number') \
	.drop('phone_numbers') \
	.show()

users_df \
	.select('id', col('phone_numbers')['mobile'].alias('mobile'), col('phone_numbers')['home'].alias('home')) \
	.show()
	
```
** Structs
```python
#Structs have predifined structurea sto compared to arrays and maps, all rows should be same structure
from pyspark.sql import Row
users = [ 
	{
		'id': 1,
		'name': John,
		'phone_numbers': Row(mobile='+3709999999', home='+37077777')
	}
]

users_df = spark.createDataFrame([Row(**user) for user in users])
# list in dictionary is created as array data type:
# phone_numbers: struct
	# mobile: string
	# home: string

#to access element in array, use col function
users_df \
	select ('id', 'phone_numbers.home',  'phone_numbers.mobile')
	.show()

from pyspark.sql.functions import col
users_df \
	select ('id', col('phone_numbers')['home'], col('phone_numbers')['mobile'])
	.show()

users_df \
	select ('id', 'phone_numbers.*')
	.show()
```

