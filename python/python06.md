---
description: 파이썬 내장함수(Built-in Functions) 2
---

# python06

## File functions

```python
# mode : w(write), r(read), a(append)
file = open("filename", "w") 
file.write("파일 내용")
file.close()
```

**`with`**문을 이용하면 with 블록을 벗어나는 순간 열린 파일 객체 file이 자동으로 close된다.

```python
# 파일 쓰기
with open("filename","w") as file:
    file.write("파일 내용")
    
# 파일 읽기
with open("filename","r") as file:
    for line in file:
        print(line)
```

{% code-tabs %}
{% code-tabs-item title="file.py" %}
```python
def write_file():
    with open("a.csv", "w", encoding="utf8") as file:
        file.write("이름,성별,나이\n")
        file.write("김일수,남,14\n")
        file.write("김이수,남,24\n")

def read_file():
    with open("a.csv","r", encoding="utf8") as file:
        for line in file:
            print("line>>", line)

write_file()
read_file()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Iterable functions

#### 1-1 Iterable <a id="1-1-iterable"></a>

* iterable 객체 - **반복 가능한 객체**
* 대표적으로 iterable한 타입 - list, dict, set, str, bytes, tuple, range

#### 1-2 Iterator <a id="1-2-iterator"></a>

* iterator 객체 - **값을 차례대로 꺼낼 수 있는 객체**입니다.
* iterator는 iterable한 객체를 내장함수 또는 iterable객체의 메소드로 객체를 생성할 수 있습니다.

`list()`, `set()`, `tuple()`, `enumerate()`

`min()`, `max()`, `sum(iter, start_value)`

`all(iter)` : 모두가 참일 때 True

`any(iter)` : 하나라도 참이면 True

`iter()` , `next()`

```bash
>>> l = [1,2,3]
>>> sum(l)
6
>>> sum(l,1)
7
# sum 대신 math 사용
>>> import math
>>> math.fsum(l)
6.0

>>> ll = [False, True, False]
>>> lll = [False, False]
>>> llll = [True, True]
>>> all(ll)
False
>>> any(ll)
True
>>> any(lll)
False
>>> l.append(0)
>>> all(l)
False
>>> any(l)
True
>>> l.pop(3)
0
>>> all(l)
True
```

```bash
>>> l
[1, 2, 3]
>>> iter(l)
<list_iterator object at 0x000001EA8391F470>

>>> it = iter(l)
>>> next(it)
1
>>> next(it)
2
>>> next(it)
3
>>> next(it) # 메모리에 더이상 없으므로 에러 발생. 
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
 
>>> it9 = iter(t)
>>> next(it9, None)
1
>>> next(it9, None)
2
>>> next(it9, None)
3
>>> next(it9, None)
4
>>> next(it9, None)
5
>>> next(it9, None) 
```

#### zip\(\)

```bash
>>> l1 = [1,2,3]
>>> l2 = [4,5,6]
>>> zip(l1, l2)
<zip object at 0x0000015FC2848048>
>>> z = zip(l1, l2)
>>> list(z)
[(1, 4), (2, 5), (3, 6)]
>>> l3 = [7,8]
>>> z = zip(l1, l3)
>>> list(z) 
[(1, 7), (2, 8)] 
```

## Filter\(\) function

1-1. lambda 함수 사용

```bash
>>> int_numbers = range(-5, 6)
>>> print(list(int_numbers))
[-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
# lambda 표현식
>>> negatives = filter(lambda x: x<0, int_numbers)
>>> negatives
<filter object at 0x0000015FC2D81470>
>>> list(negatives)
[-5, -4, -3, -2, -1]
```

1-2. 함수 사용

```bash
>>> def f(x):
...     return x < 0
...
>>> n2 = filter(f, int_numbers)
>>> list(n2)
[-5, -4, -3, -2, -1]
```

## map\(\) function

map\(mapped\_fn, iter\) : map object

```bash
>>> numbers = (1, 2, 3, 4)
>>> triple_numbers = map(lambda x: x * 3, numbers)
>>> print(list(triple_numbers))
[3, 6, 9, 12]
```

```bash
>>> def make_double(n):
...     return n * 2
...
>>> double_numbers = map(make_double, numbers)
>>> print(list(double_numbers))
[2, 4, 6, 8]
```

```python
# filter와 map 비교
int_numbers = range(-5, 6)
f = filter(lambda x : x * 2, int_numbers)
m = map(lambda x : x * 2, int_numbers)

print("f =", list(f)) # 조건이 True인 값만 취함
print("m =", list(m)) # 각각의 값에 대해서 조건을 수행하고 난 결과값
```

## reduce\(\) function

reduce\(reduce\_fn, iter\) : one result

```bash
>>> product = 1
>>> lst = [1,2,3,4]
>>> for num in lst:
...     product = product * num
...     print("product>>", product)
...
product>> 1
product>> 2
product>> 6
product>> 24
```

```bash
>>> from functools import reduce
>>> product2 = reduce(lambda x,y: x * y, lst)
>>> print("product2>> ", product2)
product2>>  24
```

## sorted\(\) 오름차순, reversed\(\) 내림차순

```bash
>>> numbers = [5,4,3,2,1]
>>> sort_numbers = sorted(numbers) 
>>> print("sort_numbers=", sort_numbers)
sort_numbers= [1, 2, 3, 4, 5]
>>> print("numbers=", numbers)
numbers= [5, 4, 3, 2, 1]
```

```bash
numbers = [5,4,3,2,1]

sort_numbers = sorted(numbers)
print("sort_numbers=", sort_numbers)
print("numbers=", numbers)

numbers.sort()
print("asc>>", numbers)

numbers.sort(reverse=True)
print("dsc>>", numbers)
```

## Sorting Objects

```python
class Student:
    def __init__(self, name, score):
        self.name = name
        self.score = score

    # toString
    def __str__(self):
        return "{}:{}".format(self.name, self.score)

students = [
    Student("김일수", 10),
    Student("김삼수", 30),
    Student("김이수", 20),
]

print(students[0])

def print_students():
    print("----------------------")
    for s in students:
        print(s)

# 내장함수 sorted
sorted(students, key=lambda stu : stu.score)
print_students()

# list의 sort함수
students.sort(key=lambda stu : stu.score)
print_students()

# lambda stu : stu.score 는
# def fn(stu):
#   return stu.score 과 같다

def sort_key(stu):
    return stu.score
students.sort(key=sort_key, reverse = True)
print_students()
```

