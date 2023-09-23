```python
mode('append' | 'overwrite' | 'ignore' | 'error')
# default - error

# ways to specify:
df.write.mode(saveMode).fileFormat('/path/')
df.write.format('/path/', mode=saveMode)
df.write.mode(saveMode).format('fileFormat').save('/path/')
df.write.format(fileFormat).save('path', mode=saveMode)
```