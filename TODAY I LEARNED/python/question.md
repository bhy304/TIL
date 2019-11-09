---
description: 문제 풀기
---

# Questions

## Q1

fruits = {'오렌지': 400, '사과': 200, '바나나': 300} 일때, 오렌지 3개, 사과 2개, 바나나 5개를 샀다면 총 구매액은??

```bash
>>> fruits = {'오렌지':400,'사과':200,'바나나':300}
>>> fruits
{'오렌지': 400, '사과': 200, '바나나': 300}
>>> fruits['오렌지']
400
>>> total = fruits['오렌지']*3 + fruits['사과']*2 + fruits['바나나']*5
>>> total
3100
```

```bash
# 변형문제
fruits={'orange':200, 'apple':300, 'banana':500}
cart = {'orange':3, 'apple':2, 'banana': 2}
>>> fruits={'orange':200, 'apple':300, 'banana':500}
>>> cart = {'orange':3, 'apple':2, 'banana': 2}
>>> total = fruits['orange']*cart['orange'] + fruits['apple']*cart['apple'] +fruits['banana']*cart['banana']
>>> total
2200
```

#### for문을 이용한 풀이방법

```python
#방법1
sum=0
for key  in cart:
   sum += fruits[key]*cart[key]
print(sum)

#방법2
sum=0
for key, value  in cart.items():
   sum += fruits[key]*value
print(sum)
```

## Q2

```bash
>>> arr = []
>>> for i in range(0,20,2):
...     arr.append(i)
...     print(i)
...
0
2
4
6
8
10
12
14
16
18
```

#### 위와 동일한 결과를 내는 코드를 한줄로 작성하세요.

#### 방법1

```bash
>>> xs = list(range(0,20,2))
>>> print(xs)
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

#### 방법2

```bash
>>> list([i for i in range(0,20,2)])
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

