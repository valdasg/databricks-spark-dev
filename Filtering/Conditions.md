```python
= or ==
!=
< or >
>=
<=
isin() or IN or contains()
between() or BETWEEN with AND
isnan() or !col("column_name").isNaN()
isNull() or isNotNull()

```

```python
df.filter(df['column'] == True).show()
#or
df.filter(df['column'] == 'true').show()
#or
df.filter('column == True').show()
# you can pass conditions as strings, even in is int, bool or whatever.
```

```python
# isnan() returns true or false
df.select('column', isnan('column')).show()
df.filter(isnan('column') == True).show()
```

```python
# between returns bool
df.select(col()'column1').between('date_from', 'date_to') 
# to get values applu bool mask to filter
df \
	.select('column1', 'columnn2') \
	.filter(col()'column1').between('date_from', 'date_to') \
	.show()
# or SQL style
df \
	.select('column1', 'columnn2') \
	.filter('column1'BETWEEN 'date_from' AND 'date_to') \
	.show()
```

```python
df.select(filter(col('column1').isnull()))
#or
df.select(filter('column1 IS NOT NULL')

```

```python
# multiple boolean conditions
OR
AND
NEGATION

# for OR if any of conditions return TRUE -> TRUE
# for AND if any of conditions return FALSE -> FALSE

df.filter((col('column1') == '') | (col('column2') == 'value'))
#or
df.filter('column1 = "" OR column2 == "value")
# or
df.filter(col('column1').isin('value1', 'value2'))
#or
df.filter("column1 IN ('value1', 'value2')") # can not have NULL in list, use chained isNull()
```

```python
# greater then, less then
df.filter(col('column') > value)
#or
df.filter('column1 > value')
```

```python
# AND
df.filter((col('colum1') == value1)) & (col('colum2') == value2)
# or SQL type syntax
df.filter('(colum1 = value1) AND (colum2 = value2)')
```