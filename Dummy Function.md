```python
def dummy_args(*args):
"Prints args as touples"
	print(args)

dummy_args(1)
>>> (1, )

user = [1, 'Tom']
dummy_args(user)
>>> ([1, 'Tom'], )

user = [1, 'Tom']
dummy_args(*user)
>>> (1, 'Tom')

```

```python
def dummy_kwrgs(**kwargs):
"Prints kwargs as touples"
	print(kwargs)

user = [{"user_id": 1, "user_name": "Tom"}]
dummy_kwargs(user)
>>> TypeError

dummy_kwargs(user = user)
>>> {'user': {'user_id': 1, 'user_name': 'Tome'}}

dummy_kwargs(**user)
>>> {user_id': 1, 'user_name': 'Tome'}

```


While using * or ** list is exploded to elements