## 🔑 Criando *Key-value Stores* utilizando *Python Dictionaries*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *

## Evitando *KeyError* com *defaultdict* 

### Exemplo de *KeyError*
```python
example_dict = {'a': 1, 'b': 2}

print(example_dict['c'])
# Traceback (most recent call last):
#  File "<stdin>", line 1, in <module>
# KeyError: 'c'
```

### Exemplo de tratamento com *if* 
```python
example_dict = {'a': 1, 'b': 2}

if 'c' in example_dict:
	print(example_dict['c'])
```

### Exemplo de tratamento com *get()*
```python
example_dict = {'a': 1, 'b': 2}

print(example_dict.get('c', 0))
# 0
```

### Exemplo com *dict()*
```python
example_dict = {}
customer_arrival_times = [('tony', 1), ('sam', 2), ('tony', 14)]

for customer, time in customer_arrival_times:
	if customer in example_dict:
		example_dict[customer].append(time)
	else:
		example_dict[customer] = []
		example_dict[customer].append(time)

print(example_dict)
# {'tony': [1, 14], 'sam': [2]}
```

### Exemplo com *defaultdict()*
```python
from collections import defaultdict

example_default_dict = defaultdict(list)
customer_arrival_times = [('tony', 1), ('sam', 2), ('tony', 14)]

for customer, time in customer_arrival_times:
	example_default_dict[customer].append(time)

print(example_default_dict.items())
# dict_items([('tony', [1, 14]), ('sam', [2])])

print(example_default_dict.get('tony'))
# [1, 14]
```

* * *

## Simplificando *Nested Dictionaries*

### Exemplo
```python
nested_dict = {
	'clients': {
		'joe': 1,
		'tom': 2
	},
	'vendors': {
		'creative_soft': 44,
		'office_space': 33
	}
}

def flatten_dict(dictionary, key_prefix='', separator='.'):
	result = []
	for k, v in dictionary.items():
		flattened_key = key_prefix + k
		if isinstance(v, dict):
			result.extend(flatten_dict(v, flattened_key + separator, separator=separator).items())
		else:
			result.append((flattened_key, v))
	return dict(result)

print(flatten_dict(nested_dict))
# {'clients.joe': 1, 'clients.tom': 2, 'vendors.creative_soft': 44, 'vendors.office_space': 33}
```
* * *

## *Mini Switch-Case* utilizando *Dictionaries*

### Exemplo
```python
def case_1():
	print('Case 1')

def case_2():
	print('Case 2')
	
def case_3():
	print('Case 3')
	
case_dict = {
	'1': case_1,
	'2': case_2,
	'3': case_3,
}

case_dict['2']() # equivalente ao switch-case do python
```
* * *

## Unindo dois dicionários de maneira simples, com apenas uma linha de código.

### *For Loop*

```python
x = {
	'a': 1,
	'b': 2
}

y = {
	'c': 3,
	'd': 4
}

z = {}

dictionaries = [x, y]

for dictionary in dictionaries:
	for key, value in dictionary.items():
		z[key] = value
	
for k, v in x.items():
	z[k] = v
	
for k, v in y.items():
	z[k] = v
 
print(z)
# {'a': 1, 'b': 2, 'c': 3, 'd': 4}
```

### Utilizando *dict()*

```python
x = {
	'a': 1,
	'b': 2
}

y = {
	'c': 3,
	'd': 4
}

print(dict(**x, **y))
# {'a': 1, 'b': 2, 'c': 3, 'd': 4}
```

* * *

## Criando um dicionário com *List Comprehension* 

### Exemplo
```python
keys = ['x', 'y', 'z']
values = [1, 2, 3]

dict([(k, v) for k, v in zip(keys, values) if k == 2])
# {'x': 1, 'y': 2, 'z': 3}

dict([(k, v) for k, v in zip(keys, values) if k == 'x'])
# {'x': 1}
```