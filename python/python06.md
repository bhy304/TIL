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

`list()`, `set()`, `tuple()`, `enumerate()`

`min()`, `max()`, `sum(iter, start_value)`

`all(iter)` : 모두가 참일 때 True

any\(iter\) : 하나라도 참이면 True

iter\(\) 

```bash
>>> l = [1,2,3]
>>> sum(l)
6
>>> sum(l,1)
7
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

