```python
# approach1:
df.write \
	.csv('/path
# approach2:
df.write \
	.format('csv') \
	.save('path')

# options: headers, delimiters (default comma), compression, mode (default - throw exception)
```

```python
# specify mode and headers
df \
	.coalesce(1) \ # create one file
	.write \
	.csv('/path/', mode='overwrite', header=True)
#or
# note options in save!
df \
	.coalesce(1) \ # create one file
	.write \
	.format('csv') \
	.save('/path/', mode='overwrite', header=True)
```

```python
# compression
df \
	.write \
	.csv(
		'/path/',
		mode='overwrite',
		compression='gzip',
		header=True
		)
# or

df \
	.coalesce(1)
	.write \
	.format('csv') \
	.save('path',
		mode='overwrite',
		compression='gzip',
		header=True)
```

```python
# delimiter (default comma, can use mode in this ay as well
df \
	.write \
	.mode('overwrite') \
	.csv('/path/', sep='|', header=True)
```

```python
# using options or options
df \
	.coalesce(1) \
	.write \
	.mode('overwrite') \ # note: overwrite as mode, not option
	.option('compression', 'gzip') \
	.option('header', True) \
	.option('sep', '|') \
	.csv('/path/')

# using options:
df \
	.coalesce(1) \
	.write \
	.mode('overwrite') \ # note: overwrite as mode, not option
	.options('compression'='gzip', 
			'header'= True,
			'sep'= '|') \
	.csv('/path/')
```

```python
options = {
		  'sep': '|',
		  'header': True
		  }
df \
	.coalesce(1) \
	.write \
	.mode('overwrite') \ # note: overwrite as mode, not option
	.options(**options) \
	.csv('/path/')
```