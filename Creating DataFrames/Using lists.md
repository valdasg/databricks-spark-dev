1. Single column from List  (need to specify schema)
```python
ages = [21, 23, 25]
spark.createDataFrame(ages, 'int')

# or

from pyspark.sql.types import IntegerType, StructType, StructField
spark.createDataFrame(ages, IntegerType())

# or
# Note that when you provide a list of data, each element in the list represents a row in the DataFrame. So you need to transform your list so that it is a list of rows, not just a list of values:
schema = StructType([StructField("Age", IntegerType())])
data = [(age,) for age in ages]
spark.createDataFrame(data, schema)
```
2. Single column using touples (no chema mandatory)
```python
ages = [(23, ), (43, ), (32, )]
spark.createDataFrame(ages)

# or if you want to specify schema

spark.createDataFrame(ages, 'age int')

```
3. Multiple column using touples (no schema is mandatory)
```python
users = [('Tom', 20), ('John', 43), ('Timothy', 32)]
spark.createDataFrame(ages)

# or if you want to specify schema

spark.createDataFrame(users, 'user_id str, age int')
```
4. Using list of lists and row
```python
from pyspark.sql import Row

users = [[1, 'Scott'], [2, 'Donald'], [3, 'Elvis']]

user_rows = [Row(*user) for user in users]
spark.createDataFrame(user_rows)

```
5. Using list of touples and row
```python
from pyspark.sql import Row
users = [(1, 'Scott'), (2, 'Donald'), (3, 'Elvis')]

user_rows = [Row(*user) for user in users]
spark.createDataFrame(user_rows)

```
6. Using list of dictionaries and row
```python
from pyspark.sql import Row
users = [
		 {user_id: 1, 'first_name': 'Scott'},
		 {user_id: 2, 'first_name':'Donald'},
		 {user_id: 3, 'first_name':'Elvis'}
		 ]

# use values() as a part of dict to get list type object
user_details = users[0]
>>> {user_id: 1, 'first_name': 'Scott'}

r_user_details = users[0].values()
>>> dict_values([1, 'Scott'])

r = Row(*r_user_details)
>>> Row(2, 'Scott')

user_rows = [Row(*user.values()) for user in users]
spark.createDataFrame(user_rows)

```
```python
# using *kwargs
user_rows = [Row(**user) for user in users]
spark.createDataFrame(user_rows)
```
