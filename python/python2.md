---
description: 'Composite Operation, Casting, 자료구조(List, Tuple, Dictionary)'
---

# python02

## Composite Operation 복합연산자

```bash
>>> x = 30
>>> x += 10
>>> print(x)
40
>>> x -= 10
>>> print(x)
30

>>> x++
  File "<stdin>", line 1
    x++
      ^
SyntaxError: invalid syntax
# Python에서는 x++, x-- 사용할 수 없다!
```

```bash
>>> x = 1
>>> x += 1 # x++ , x = x + 1
>>> print(x)
2
>>> x -= 1 # x-- , x = x - 1
>>> print(x)
1
```

```bash
>>> s = "안녕하세요"
>>> s += "Hi~"
>>> print(s)
안녕하세요Hi~
```

## Casting 형변환

```bash
# String to Int or Float
>>> si, sf = "3", "3.5"
>>> i, f = int(si), float(sf)
>>> print(i, f)
3 3.5
>>> print(type(i), type(f))
<class 'int'> <class 'float'>

>>> si, sf = "3", "3.5"
>>> float(sf)
3.5
>>> float(si)
3.0
>>> str(23)
'23'
>>> type(str(23))
<class 'str'>
```

## List

```bash
>>> fruits = ['오렌지','사과','바나나'] #1차원Array
>>> fruits[1]
'사과'
>>> fruits[0:2]
['오렌지', '사과']
>>> fruits[-1]
'바나나'
>>> prices = [300, 400, 500] #1차원Array
>>> prices
[300, 400, 500]
>>> [ fruits[1], prices[1] ] 
['사과', 400]

#2차원Array
>>> [ fruits, prices ]
[['오렌지', '사과', '바나나'], [300, 400, 500]]

>>> items = fruits + prices
>>> items
['오렌지', '사과', '바나나', 300, 400, 500]

>>> fruits.append('체리')
>>> fruits
['오렌지', '사과', '바나나', '체리']
>>> things = ['오렌지', 90, '바나나', 30]
>>> items.extend(things)
>>> items
['오렌지', '사과', '바나나', 300, 400, 500, '오렌지', 90, '바나나', 30]
>>> len(items)
10
>>> len(items[0])
3
>>> fruits[0][1]
'렌'

>>> fruits.insert(1,'포도')
>>> fruits
['오렌지', '포도', '사과', '바나나', '체리']

>>> fruits.pop(1)
'포도'

>>> a = del fruits[1]
  File "<stdin>", line 1
    a = del fruits[1]
          ^
SyntaxError: invalid syntax

>>> a = fruits.pop(1)
>>> a
'사과'
>>> fruits
['오렌지', '바나나', '체리']
>>> fruits.remove('바나나')
>>> fruits
['오렌지', '체리']
>>> fruits.clear()
>>> fruits
[]
>>> print("has 사과", '사과' in fruits)
has 사과 False
>>> print("has 사과", '사과' not in fruits)
has 사과 True
```



