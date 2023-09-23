```python
# can be acheved with:
# - alias as part of select
# - using withColumn on top of dataframe to perform row level operations. If column name given is the same it will be overwritten.
# - to just remane column use withColumnRenamed
# - to rename multiple columsn use toDF

from pyspark.sql.functions import col, lit, concat, size

# using alias
users_df \ 
	.select('id', 'first_name', 'last_name', concat('first_name', lit(' '), 'last_name').alias('full_name')) \
	.show()

# using withColumn
users_df \ 
	.select('id', 'first_name', 'last_name') \
	.withColumn('full_name', concat('first_name', lit(' '), 'last_name'))
	.show()

users_df \ 
	.select('first_name') \
	.withColumn('first_name', col('first_name')))
	.show()
	
users_df \ 
	.select('id', 'courses') \
	.withColumn('course_count', size(col('courses'))
	.show()

# using withColumnRenamed, useful when renaming single column
users_df \ 
	.withColumnRenamed('first_name', 'name') \
	.withColumnRenamed('last_name', 'surname') \
	.show()

# using toDF
required_columns = ['id', 'first_name', 'last_name']
target_column_names = ['user_id', 'user_first_name', 'user_last_name']

# toDF does not take list as argument, use *
users_df 
	.select(required_columns) \
	.toDF(*target_column_names)
	.show()

```