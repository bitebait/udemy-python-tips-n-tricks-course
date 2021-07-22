## 🚀 Acelerando seu código com *High Performance Container Datatypes*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *
### Sem *Counter*
```python
from collections import defaultdict

word_list = ['apple', 'apple', 'banana', 'coconut', 'banana', 'kiwi']

counts = defaultdict(int)

for word in word_list:
	counts[word] += 1

print(counts)
# defaultdict(<class 'int'>, {'apple': 2, 'banana': 2, 'coconut': 1, 'kiwi': 1})
```

### Com *Counter*
```python
from collections import Counter

word_list = ['apple', 'apple', 'banana', 'coconut', 'banana', 'kiwi']

print(Counter(word_list).most_common(1))
# [('apple', 2)]
```

* * *

## Criando *Stacks* ou *Queues* com *Deque Objects*

### Exempo
```python
from collections import deque

x = deque('abcdef')
print(x)
# deque(['a', 'b', 'c', 'd', 'e', 'f'])

x.appendleft('1')
print(x)
# deque(['1', 'a', 'b', 'c', 'd', 'e', 'f'])

x.pop()
print(x)
# deque(['1', 'a', 'b', 'c', 'd', 'e'])

x.popleft()
print(x)
# deque(['a', 'b', 'c', 'd', 'e'])

print(x[0])
# a

x.rotate(2)
print(x)
# deque(['d', 'e', 'a', 'b', 'c'])

x.reverse()
print(x)
# deque(['c', 'b', 'a', 'e', 'd'])
```

* * *
## Agrupamento de Valores Relacionados com *Tuplas* e *Sequências*

### Exemplos

```python
example_tuple = (44, 'a string')

print(example_tuple)
# (44, 'a string')
```

```python
singleton = (44,)

print(singleton)
# (44,)
```

```python
def function_returning_multiple_values():
	return (4, 5)

x, y = function_returning_multiple_values()

print(x)
# 4
print(y)
# 5
```

```python
x, y, z = 1, 2, 3

print(x)
# 1
print(y)
# 2
print(z)
# 3
```

```python
def function_returning_multiple_values():
	return (4, 5)

x, _ = function_returning_multiple_values
print(x)
# 4
```

* * *
## Reunindo conjuntos únicos de valores com *Sets* e *Frozensets*

### Exemplo *Sets*
```python
x = [1, 2, 3, 4, 1, 2]

print(set(x))
# {1, 2, 3, 4}
```

```python
x = [1, 2, 3, 4, 1, 2]

unique_x = list(set(x))
unique_x.append(2)

print(unique_x)
# [1, 2, 3, 4, 2]
```

### Exemplo *Frozensets*
```python
key_frozenset = frozenset([1, 2, 3])

print({ key_frozenset: 4 })
# {frozenset({1, 2, 3}): 1}
```

* * *

## Dicionários Ordenados

### Exemplo
```python
d1 = {}
d1['1'] = '1'
d1['2'] = '2'
d1['3'] = '3'

d2 = {}
d2['3'] = '3'
d2['2'] = '2'
d2['1'] = '1'

print(d1 == d2)
# True
```

```python
import collections

d1 = collections.OrderedDict()
d1['1'] = '1'
d1['2'] = '2'
d1['3'] = '3'

d2 = collections.OrderedDict()
d2['3'] = '3'
d2['2'] = '2'
d2['1'] = '1'

print(d1 == d2)
# False
```