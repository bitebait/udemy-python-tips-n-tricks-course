## 🧪 Facilitando o *Debug* do seu código com *Functional Programming*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *

## Como fazer chamadas de função com *arguments* e *kwargs* 

### *Typical Function*
```python
def typical_func(one, two, three):
	'''
	Args:
	one, two, three str: string
	'''
	return one + two + three

print(typical_func('mary', 'had a', 'little lamb'))
# maryhad alittle lamb

start = 'mary'
#bunch of code
middle = 'had a'
#bunch of code
end = 'little lamb'

arguments = (start, middle, end)

print(typical_func(*arguments))
# maryhad alittle lamb

print(typical_func(start, middle, end))
# maryhad alittle lamb
```

### Utilizando *kwargs*
```python
def kw_functions(a=1, b=2):
    return a + b

print(kw_functions(a=1, b=30))
# 31

things_to_add = {
    'a': 10,
    'b': 20
}

print(kw_functions(**things_to_add))
# 30
```

* * *

## *One line functions* com *lambdas*

### Exemplos
```python
import functools

x = [12, 318, 29, 122, 417, 204]

filter_example = list(filter(lambda x: x % 3 == 0, x))

print(filter_example)
# [12, 318, 417, 204]


# List Comprehension - [x * 2 for x in x]
map_example = list(map(lambda x: x * 2, x))

print(map_example)
# [24, 636, 58, 244, 834, 408]


print(functools.reduce(lambda x, y: x + y, x))
# 1102
```

* * *

## Utilizando funções dentro de funções para segmentar seu código

### Exemplo de uma função normal
```python
def normal_f():

    def get_animal():
        return 'zebra'

    return 'There is a {animal}.'.format(animal=get_animal())


print(normal_f())
```

### Exemplo funções dentro de funções 
```python
def process_file(filename):

    def computed_new_data(some_data):
        return some_data.replace('#', '<hashtag>')

    with open(filename, 'r') as f:
        data = f.read()
        result = computed_new_data(data)

    return result
```

* * *

## Criar funções dinâmicas retornando funções

### Exemplo não dinâmico
```python
def custom_operator(x):
    return (x + 2) ** 2


def custom_operator_2(x):
    return (x + 3) ** 2


print(custom_operator_2(10))
# 169
```

### Exemplo dinâmico

```python
def custom_operator_maker(increment=2, power=2):
    def return_this_func(x):
        return (x + increment) ** power
    return return_this_func


f1 = custom_operator_maker()
f2 = custom_operator_maker(3, 2)

print(f1(10))
# 144

print(f2(10))
# 169
```

* * *

##  Utilizando *Decorators*

### Exemplo
```python
def some_decorator(f):

    def function_wrapper():
        print('before')
        f()
        print('after')

    return function_wrapper


def some_function():
    print('This is some_function')


wrapped_function = some_decorator(some_function)

print(wrapped_function())
# before
# This is some_function
# after


@some_decorator
def some_other_function():
    print('This is some_other_function')


print(some_other_function())
# before
# This is some_other_function
# after
```