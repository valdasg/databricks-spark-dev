```python

# all pyspark.sql.functions return col type objects
from pypspark.sql.functions import col, lit, contact


ful_name_col = concat(col('first_name'), lit(' '), col('last_name')) \
full_name_alias = full_name.alias('full_name')

users_df \
	.select('id', full_name_alias) \
	.show()
```