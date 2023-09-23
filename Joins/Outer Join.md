```python
#outer means full outer join, use left, left_outer  or leftouter
df \
	.join(df1, 'id', 'left')

#or

df \
	.join(df1, df.id == df1.id, 'left')

# note that columns are displayed based on join type, left displays left, right - right
```