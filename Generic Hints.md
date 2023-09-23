1. Dataframes can be created from: 
	-  list (single column)
	- list of lists
	- list of tuples
	- RDDs
	- list of dictionaries
	- list of rows
	- pandas DF
2. Schemas can be specified:
	- using string
	- using DDL format string
	- using StructType and list StructField functions
	- using list (however, only column names are passed)
	- inferring schema (not possible with when single column data frame is created from list )
3. Use **col()** function when transformation is needed. String operations do not require **col()**. Data being in columns, does not mean it is **col** type. However if you refer any data in column using df.column or df['column'] it will be treated as col type object and it is not needed to use col() on it anymore.
4. Use **lit()** function to convert anything to literal to be applicable on columns.
5. **broadcast()** is a function and not a join type
6. When using functions on columns (like explode()) make sure, it is a part of select. These functions are not dataframe methods.
7. **collect()** does not take any arguments and return list of rows, **take()** takes arguments and also returns list.
8. There are two ways to sort. However, you can not chain things like .desc_nulls_last() to first line as all these functions require col type object to be returned as result of previous chain task Alias for sort() is orderBy(). `orderBy` accepts both strings (column names) and column objects. If you need to perform more complex sorts, such as sorting in descending order or handling null values in a specific way, you need to use a column object. 

```python
sort('column_name', asceeding = False)
#or
sort(col('column_name')).desc()
# sort two columns
df.sort(df.column1.desc(), df.column2.asc())
# in case you use asc_nulls_first() or similar, chain it to column, it does not take any arguments.
```

1. Variables come without quotes and other things in quotes:
```python
spark \
	.read \
	.schema(schema=schema) \
	.fromat('parquet') \
	.load(filePath)
```
1. distinct() and dropDuplicates() are the same dataframe methods, except that dropDuplicates() takes argument list or subset of columns. If it is omitted, it will return same result as distinct().
2. When using **udf()** you can omit return type if it is expected to return string, as it is default type.
3. When using DataFrame.sample(withReplacement=None, fraction=None, seed=None): withReplacement - option specifying if after sampling we put row back to df, fraction - fraction taken, seed - if same seed is used, same results will be obtained.
4. drop() takes columns as arguments, not list. Also, if column is not available, it is ignored and error is not thrown.
5. Function **spark.conf.set()** takes strings as parameters.

