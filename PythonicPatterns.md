## 🧼 Criando aplicações mais seguras e limpas com *Pythonic Patterns*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *

## Enumerando os índices de seus *loops* sem linhas extras

###   

```python
names = ['Angela', 'John', 'Mary', 'Sam']

for i, name in enumerate(names):
    print("{}. {}".format(str(i + 1), name))
	
# 1. Angela
# 2. John
# 3. Mary
# 4. Sam
```

* * *

## Enfatize variáveis inúteis para tornar seu código mais fácil de ler

###   

```python
def some_function():
    # returns name, best language, work experience
    return "John", "Java", 12

_, language, years = some_function()

summary_statistics = {}
summary_statistics[language] = 0
summary_statistics[language] += years

print(summary_statistics)
# {'Java': 12}

for age, _, _, language in careers:
    pass

```

* * *

## *for..else loop* incomum para acabar com sua iteração

###   

```python
xs = [1, 2, 3, 4, 5]

print([x for x in xs if x == 3])
# [3]

filtered_xs = [x for x in xs if x == 10]
if len(filtered_xs) == 0:
    print('No match')
else:
    print('Matched.')

# No match

filtered_xs = []
for x in xs:
    if x == 10:
        filtered_xs.append(x)
else:
    print('No match')

# No match

```

* * *

## Imprimindo qualquer estrutura de dados *Python*

###   

```python
from pprint import pprint as _p

x = [1, 2, [3, 4, 5, 'knight', [3, 4, 5, 'knight']], 15]

print(x)
# [1, 2, [3, 4, 5, 'knight', [3, 4, 5, 'knight']], 15]

_p(x, width=20, indent=4, depth=1)
# [1, 2, [...], 15]

_p(x, width=30, depth=4)
# [   1,
#     2,
#     [   3,
#         4,
#         5,
#         'knight',
#         [3, 4, 5, 'knight']],
#     15]

```

* * *

## Gerenciando seus recursos dinâmicos cuidadosamente com *context managers*

###   

```python
# testing
def dummy_test(self):
    with self.assertRaises(TypeError):
        ' '.join(2)

		
# threading
def threading.RLock(self):
    access_resource()

# connecting to external resources
conn = sqlite3.connect(':memory:')
with conn:
    conn.execute('select * from table')
```
