## 📝 Trabalhando *Ordered Collections* com  *Lists* e *List Comprehension*

** *Exemplos retirados do curso ["Python Tips, Tricks and Techniques - Udemy"](https://www.udemy.com/course/python-tips-tricks-and-techniques)*

<br>

* * *
## Utilizando *List Comprehension* para encurtar For Loops

### *For Loop*
```python
nums = [1, 2, 3, 4, 5]
result = []
for num in range(len(nums)):
	result.append(nums[num] * 2)

print(result)
# [2, 4, 6, 8, 10]
```

### *List Comprehension*
```python
nums = [1, 2, 3, 4, 5]

#  [action / for declaration]
result = [(num * 2) for num in nums] 

print(result)
# [2, 4, 6, 8, 10]
```

* * *

## Inserindo If Statements utilizando *Conditional List Comprehension*

### *For Loop*
```python
nums = [1, 2, 3, 4, 5]
result = []

for num in range(len(nums)):
	if nums[num] % 2 == 0:
		result.append(nums[num] * 2)
	else:
		result.append(nums[num])

print(result)
# [1, 4, 3, 8, 5]

```

### *List Comprehension*
```python
nums = [1, 2, 3, 4, 5]

result = [(num * 2 if num % 2 == 0 else num) for num in nums]

print(result)
# [1, 4, 3, 8, 5]
```

### *List Comprehension* (Filtering)
```python
nums = [1, 2, 3, 4, 5]

# [action / for declaration / conditional ] --> filtering
result = [num * 2 for num in nums if num % 2 == 0] 

print(result)
# [4, 8]
```

* * *

## Trabalhando com *Lists of Lists* utilizando *Nested List Comprehension*

### *For Loop*
```python
items = [
	[1, 2],
	[3, 4],
	[5, 6]
]
result = []

for nums in items:
	for num in nums:
		if num % 2 == 0:
			result.append(num)

print(result)
# [2, 4, 6]
```

### *List Comprehension*
```python
items = [
	[1, 2],
	[3, 4],
	[5, 6]
]

first_result = [[num for num in nums if num % 2 == 0] for nums in items]
print(first_result)
# [[2], [4], [6]]

last_result = [num for nums in items for num in nums if num % 2 == 0]
print(last_result)
# [2, 4, 6]

```

* * *

## Simplificando *Collapsed Nested Lists*

### *For Loop*
```python
items = [
	[1, 2],
	[3, 4],
	[5, 6]
]
result = []

for nums in items:
	for num in nums:
		result.append(num)

print(result)
# [1, 2, 3, 4, 5, 6]
```

### *List Comprehension*
```python
items = [
	[1, 2],
	[3, 4],
	[5, 6]
]
result = [num for nums in items for num in nums]

print(result)
# [1, 2, 3, 4, 5, 6]
```

### *chain() function*
```python
import itertools
items = [
	[1, 2],
	[3, 4],
	[5, 6]
]
result = list(itertools.chain(*items))

print(result)
# [1, 2, 3, 4, 5, 6]
```
* * *

## Truques com *List Slice*

### *For Loop*
```python
nums = [1, 2, 3, 4, 5]

# list[sart:stop:step]

# Começa em 0 e termina em 3.
print(nums[0:3])
# [1, 2, 3]

# Começa em 0 e termina em 3..
print(nums[:3])
# [1, 2, 3]

# Começa em 3.
print(nums[3:])
# [4, 5]

# Começa em 0, termina em 5 e avança de 1 em 1.
print(nums[0:5:1])
# [1, 2, 3, 4, 5]

# Começa em 0, termina em 5 e avança de 2 em 2.
print(nums[0:5:2])
# [1, 3, 5]

# Começa em 0, termina em 5 e avança de 3 em 3.
print(nums[0:5:3])
# [1, 4]

# Começa em -2.
print(nums[-2])
# 4

# Começa em 0, termina em -3.
print(nums[:-3])
# [1, 2]

# Começa em -3.
print(nums[-3:])
# [3, 4, 5]

# Avança de -1 em -1.
print(nums[::-1])
# [5, 4, 3, 2, 1]

# Começa em -3 e avança de -1 em -1
print(nums[-3::-1])
# [3, 2, 1]
```