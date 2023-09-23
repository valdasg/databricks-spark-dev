```python
# sort by specific 
df.sort(*cols, **kwargs) cols: list, str or col()
#or
df.orderBy()

# There are multiple ways to sort:
df.sort(df.column.asc())
df.sort('column', ascending = True)
df.sort(asc('column'))
df.sort(['column1', 'column2'], ascending=[0,1]) #0 - descending, 1 - ascending. It does not matter which keyword you use (ascending or descending) result will be the same, but will fail if keyword is not used and is only passed as list.

# sort ascending (default)
df.sort('column1').show()
df.sort(df['column1']).show()
df.sort(col('column1').show()
df.sort(size('column')).show()
df.sort(asc('column').show()

# sort descending
df.sort('column1', ascending = False).show() # note: ascending=false, descending = true or false will not work at all
df.sort(df['column1'].desc()).show()
df.sort(col('column1').desc().show()
df.sort(size('column').desc()).show()
df.sort(desc('column').show()
		
# dealing with nulls
# null related functions are column based
df.sort(df['column1']).asc_nulls_last().show
df.sort(df['column1']).desc_nulls_first().show


# composite sorting with multiple columns
# ascending
df \
	.sort('column1', 'column2') \
	.show()
# or
df \
	.sort(df['column1'], df['column2']) \
	.show()
# or
df \
	.sort(['column1', 'column2']) \
	.show()

# descending
df \
	.sort(desc('column1'), 'column2') \
	.show()
# or
df \
	.sort(df['column1'].desc(), df['column2']) \
	.show()
# or
df \
	.sort(['column1', 'column2'], ascending = [1,0]) \
	.show()

# prioritised sorting
level = when(col('level') == 'starter', 0).othrewise(when(col('level') == 'medium', 1).otherwise(2))

df \
	.sort(level, col('column1').desc()) \
	.show()
```