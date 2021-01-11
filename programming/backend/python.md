# Python

## Tips and tricks

1. Ternary operator

```python
x = 1 if condition else 0
```

1. Large numbers

```python
num = 10000000000
```

* is same as:

```python
num = 10_000_000_000
```

* and to print it:

```python
print(f'{total:,}')
```

1. Context manager

```python
with open('test.txt', 'r') as f:
  file_contents = f.read()

words = file_contents.split(' ')
word_count = len(words)
print(word_count)
```

* When managing resources \(files, database, streams\) consider using context manager

1. Access index in for loop

```python
arr = ['one', 'two', 'three']

for index, num in enumerate(arr, start = 0):
  print(index, num)
```

1. Loop through 2 or more arrays

```python
names = ['Peter Parker', 'Bruce Wayne', 'Barry Allen']
heroes = ['Spiderman', 'Batman', 'Flash']

for name, hero in zip(names, heroes):
  print(f'{name} is {hero}')
```

1. Unpacking

```python
a, b = (1, 2)
a, _ = (1, 2) # if second var is not used
a, b, *c = (1, 2, 3, 4, 5) # c is everthing else in array
a, b, *_ = (1, 2, 3, 4, 5)
a, b, *c, d = (1, 2, 3, 4, 5)
```

1. Class attributes access

```python
class Person():
  pass

person = Person()

first_key = 'first'
first_val = 'Alex'

setattr(person, first_key, first_val)

first = getattr(person, first_key)
```

1. Hide password or input

```python
from getpass import getpass

username = input('username')
password = getpass('password')
```

## virtualenv

### Frequently used commands
Old way
* `pip install virtual env`
* `virtualenv ENV`
* `source ENV/bin/activate`
* `pip list`
* `deactivate`

New way

* mkdir project
* python3 -m venv project/venv
* source project/venv/bin/activate
* python3 -m pip install --upgrade pip
* pip freeze > requirements.txt
* pip install -r requirements.txt
* deactivate

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

