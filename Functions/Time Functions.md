```python
from pyspark.sql.functions import to_date, to timestamp

# converts non standat to standard formats
df.select(to_date(column_name, format))
df.select(to_timestamp(column_name, format))

```

```python
# Arithmetics functions to add delta, accepts col and strings
from pyspark.sql.functions import date_add, date_sub

df.select(date_add('date column', days_to_add))

df.select(date_diff('date_from', 'date_to'))

# other functions: months_between, add_months
df.select(months_between('start_date', 'end_date', roundOff=True))

```

```python
# truncate dates
# truncate to beginning of month, yy for year, returns date
from pyspark.sql.functions import trunc, date_trunc
df \
	.withColumn('date', trunc('date', 'MM'))

# truncate to beginning of month, yy for year, returns timestamp, format goes first

df \
	.withColumn('date', date_trunc('second', 'date'))
```

```python
# Extract dates, takes col in format of date and not timestamp as argument
from pyspark.sql.functions import current_date, year, month, weekofyear, dayofyear, dayofmonth, dayofweek

s
df \
	.select(
		year('date')) \
		dayofmonth('date')
```

```python
# converting to statndard dates and timestamp
from pyspark.sql.functions import to_date, to_timestamp
# date(col, fromat)
df \
	.withColun('to_date', to_date(col('date').cast('string'), 'yyyyMMdd'))

```

```python
# change date fromat
from pyspark.sql.functions import date_format
# date_format(col, format)

df \
	.withColumn('date_ym', date_format('date_ym', 'yyyyMM'))
``

```python
# unix time is calculated from Jan 1st 1970 UTC. Beginning is called Epoch and incremented by 1 every second
# to convert unix_timestamp(col('timestamp').cast(string)), format_of_column)
# to convert back from_unixtime('unix_time', format)
# you can not cast unixtime to date, but you can to timestamp

from pyspark.functions.sql import unix_timestamp
df \
	.withColumn('unix_date', unix_timestamp(col('date').cast('string'), 'yyyyMMdd'))
```