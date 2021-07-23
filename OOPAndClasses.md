##  🧱 Organizando melhor seu código com *OOP* e *Classes*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *

## Como copiar e clonar objetcs da maneira certa.

###   Exemplo (Problema: Altera a lista original)

```python
original = [[1, 2], [3, 4]]

copy = original
copy.append([5, 6])

print(copy)
# [[1, 2], [3, 4], [5, 6]]

print(original)
# [[1, 2], [3, 4], [5, 6]]
# Lista original alterada!
```

###  *Shallow Copy* (Problema: altera lista original em nível mais profundo)

```python
original = [[1, 2], [3, 4]]

# Lista original não afetada.
shallow_copy = list(original)
shallow_copy.append([7])

print(original)
# [[1, 2], [3, 4], [5, 6]]

print(shallow_copy)
# [[1, 2], [3, 4], [5, 6], [7]]

# Lista original afetada!
shallow_copy[0][0] = 'XYZ'

print(original)
# [['XYZ', 2], [3, 4], [5, 6]]

print(shallow_copy)
# [['XYZ', 2], [3, 4], [5, 6], [7]]
```

### *Deepcopy*

```python
import copy

original = [['XYZ', 2], [3, 4], [5, 6]]

deepcopied_list = copy.deepcopy(original)

deepcopied_list.append([7, 8])

print(original)
# [['XYZ', 2], [3, 4], [5, 6]]

print(deepcopied_list)
# [['XYZ', 2], [3, 4], [5, 6], [7, 8]]

deepcopied_list[0][0] = 'ABC'

print(original)
# [['XYZ', 2], [3, 4], [5, 6]]

print(deepcopied_list)
# ['ABC', 2], [3, 4], [5, 6], [7, 8]]
```

* * *

## *Mini-classes* do Python - *namedtuples*

### Exemplo

```python
import collections

miniclass = collections.namedtuple('Mini', 'name job experience')

mini_1 = miniclass(name='joe', job='programmer', experience=20)

print(mini_1.job)
# programmer
```

* * *

## Como criar valores inteligentes com métodos e propriedades estáticas

### *Staticmethod*

```python
class TextPreprocessing:

    def remove_aprostrophe(self, word):
        return word.replace("'", "")

    @staticmethod
    def remove_spaces(word):
        return word.replace(" ", "")

preprocessor = TextPreprocessing()

print(preprocessor.remove_aprostrophe("Rudy's"))
# Rudys

print(TextPreprocessing.remove_spaces("mary had a little lamb"))
# maryhadalittlelamb
```

###  *Property*

```python
class NumberStore:
    
    number = 0
    
    def __init__(self, n):
        self.number = n
        
    def get_number(self):
        print('Number stored: {}'.format(self.number))
        
    @property
    def decorated_number(self):
        return 'Number stored: {}'.format(self.number)
        
ns = NumberStore(10)

print(ns.decorated_number)
# Number stored: 10
```

* * *

## Comparando dois diferentes objetos

### Exemplo

```python
class Programmer:
    lang = ''
    experience = 0

    def __init__(self, lang, experience):
        self.lang = lang
        self.experience = experience

    def __eq__(self, compared):
        return self.lang == compared.lang and self.experience == compared.experience

    def __ne__(self, compared):
        return (self.lang != compared.lang) or (self.experience != compared.experience)

programmer1 = Programmer('Java', 10)
programmer2 = Programmer('Java', 10)

print(programmer1 == programmer2)
# False

programmer3 = programmer2

print(programmer3 == programmer2)
# True

p1 = Programmer('Python', 5)
p2 = Programmer('Python', 5)
p3 = Programmer('Elixir', 5)

print(p1 == p2)
# True

print(p2 == p3)
# False
```

* * *

## OOP implementando *Abstract Base Classes* em *Python*.

### Exemplo

```python
from abc import ABC, abstractmethod

class Car(ABC):

    def go(self):
        print('vruuum!')

    @abstractmethod
    def speed(self):
        pass

class GenericCar(Car):

    def speed(self):
        print('60km/h')

class FastCar(Car):

    def speed(self):
        print('180km/h')

car1 = GenericCar()
car2 = FastCar()

car1.go()
# vruuum!

car1.speed()
# 60km/h

car2.go()
# vruuum!

car2.speed()
# 180km/h

```
