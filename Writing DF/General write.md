```python
# two options: write.[format] or format([format]) + save (/path/)
# analize schema
# check permissions
# overwrite, append, ignore or throw exception
# compress or not
# default compression or not (csv and json not compressed, paquet compressed)
# use right APIs and arguments
 df \
	.write \
	.json('/path/', mode='overwrite')

# or

df \
	.write \
	.format('json') \
	.save('/path/', mode='overwrite')
```