## Ternary operator

```python
x = 1 if condition else 0
```

## Large numbers

```python
num = 10000000000
```

* is same as:

```python
num = 10_000_000_000
```

* and to print it with commas:

```python
print(f'{num:,}')
```

## Context manager

{% hint style="info" %}
When managing resources \(files, database, streams\) consider using context manager
{% endhint %}

```python
with open('test.txt', 'r') as f:
  file_contents = f.read()

words = file_contents.split(' ')
word_count = len(words)
print(word_count)
```


## Access index in for loop

```python
arr = ['one', 'two', 'three']

for index, num in enumerate(arr, start = 0):
  print(index, num)
```

## Loop through 2 or more arrays

```python
names = ['Peter Parker', 'Bruce Wayne', 'Barry Allen']
heroes = ['Spiderman', 'Batman', 'Flash']

for name, hero in zip(names, heroes):
  print(f'{name} is {hero}')
```

## Unpacking

```python
a, b = (1, 2)
a, _ = (1, 2) # if second var is not used
a, b, *c = (1, 2, 3, 4, 5) # c is everthing else in array
a, b, *_ = (1, 2, 3, 4, 5)
a, b, *c, d = (1, 2, 3, 4, 5)
```

## Class attributes access

```python
class Person():
  pass

person = Person()

first_key = 'first'
first_val = 'Alex'

setattr(person, first_key, first_val)

first = getattr(person, first_key)
```

## Hide password or input

```python
from getpass import getpass

username = input('username')
password = getpass('password')
```

## virtualenv

* `mkdir project`
* `python3 -m venv project/venv --upgrade-deps`
* `source project/venv/bin/activate`
* `python3 -m pip install -U autopep8`
* `pip freeze > requirements.txt`
* `pip install -r requirements.txt`
* `deactivate`

### Save dependencies to requirements

`pip freeze --local requirements.txt`

### Specify version of python

`virtualenv -p /usr/bin/python2.6 py2_project`

## Flask

### Basic app

```python
from flask import Flask
app = Flask(__main__)


@app.route("/")
def hello():
    return "hello"
```

```bash
export FLASK_APP=main.py
flask run
```

### Turn on debug mode

`export FLASK_DEBUG=1`

