---
description: '자료구조(List, Tuple, Dictionary), if condition, for loop, while loop'
---

# python02

## List : \[ \]

```bash
>>> fruits = ['오렌지','사과','바나나'] #1차원Array>>> fruits[1]'사과'>>> fruits[0:2]['오렌지', '사과']>>> fruits[-1]'바나나'>>> prices = [300, 400, 500] #1차원Array>>> prices[300, 400, 500]>>> [ fruits[1], prices[1] ] ['사과', 400]#2차원Array>>> [ fruits, prices ][['오렌지', '사과', '바나나'], [300, 400, 500]]>>> items = fruits + prices>>> items['오렌지', '사과', '바나나', 300, 400, 500]>>> fruits.append('체리')>>> fruits['오렌지', '사과', '바나나', '체리']>>> things = ['오렌지', 90, '바나나', 30]>>> items.extend(things)>>> items['오렌지', '사과', '바나나', 300, 400, 500, '오렌지', 90, '바나나', 30]>>> len(items)10>>> len(items[0])3>>> fruits[0][1]'렌'>>> fruits.insert(1,'포도')>>> fruits['오렌지', '포도', '사과', '바나나', '체리']>>> fruits.pop(1)'포도'>>> a = del fruits[1]  File "<stdin>", line 1    a = del fruits[1]          ^SyntaxError: invalid syntax>>> a = fruits.pop(1)>>> a'사과'>>> fruits['오렌지', '바나나', '체리']>>> fruits.remove('바나나')>>> fruits['오렌지', '체리']>>> fruits.clear()>>> fruits[]>>> print("has 사과", '사과' in fruits)has 사과 False>>> print("has 사과", '사과' not in fruits)has 사과 True
```

## Tuple : \( \)

#### Tuple은 Read Only List

```bash
>>> fruits = ['오렌지', '사과', '바나나']>>> fruits[0], fruits[1]('오렌지', '사과')>>> q = fruits[0], fruits[1]>>> q('오렌지', '사과')
```

```bash
>>> fruits = ('오렌지','사과','바나나')>>> fruits('오렌지', '사과', '바나나')>>> x, y = 1, 2>>> (x,y)(1, 2)
```

```bash
>>> fruits = ('오렌지','사과','바나나')>>> fruits[0:2]('오렌지', '사과')>>> fruits[1]'사과'# Tuple에서는 append 사용할 수 없다.>>> fruits.append('bbb')Traceback (most recent call last):  File "<stdin>", line 1, in <module>AttributeError: 'tuple' object has no attribute 'append'#AttributeError는 어떠한 값에 대한 에러!
```

## Dictionary **: { }**

#### **Hash Map, key: value, JSON**

```bash
>>> fruits = {'사과':400, '바나나':200, '파인애플':500}>>> fruits{'사과': 400, '바나나': 200, '파인애플': 500}>>> fruits.keys()dict_keys(['사과', '바나나', '파인애플'])>>> fruits.values()dict_values([400, 200, 500])>>> fruits['바나나']200>>> '바나나' in fruitsTrue>>> 200 in fruitsFalse # "in"은 key에서만 찾는다!
```

#### Try this!

"오렌지 3개, 사과 2개, 바나나 5개를 샀다면 총 구매액은?"

```bash
>>> fruits = {'오렌지':400, '사과':200, '바나나':300}>>> total = fruits['오렌지']*3 + fruits['사과']*2 + fruits['바나나']*5>>> total3100
```

#### 응용 문제

```bash
>>> fruits={'orange':200, 'apple':300, 'banana':500}>>> cart = {'orange':3, 'apple':2, 'banana': 2}>>> total = fruits['orange']*cart['orange'] + fruits['apple']*cart['apple'] +fruits['banana']*cart['banana']>>> total2200
```

## if condition

{% tabs %}
{% tab title="test\_if.py" %}
```python
score = 80if score > 70:    print('합격')    print('축하합니다!')elif score == 70:    print('합격도 아니고 불합격도 아님!')else:    print('불합격')    print('다음 기회에 응시해주세요.')
```
{% endtab %}
{% endtabs %}

## for each loop

```python
for i in range(1, 100):    print(i)
```

```bash
>>> fruits = ['오렌지','사과','바나나']>>> for x in fruits:...     print(x)...오렌지사과바나나
```

```bash
>>> for i in range(0,3):...     print(fruits[i])...오렌지사과바나나
```

## While loop

무한 루프\(loop\)

> 무한 루프란 무한히 반복한다는 의미

```text
while (True):    수행할 문장 
```

> while문의 조건문이 True이므로 항상 참이 된다. 따라서 while문 안에 있는 문장들은 무한하게 수행될 것이다.

```bash
>>> i, sum = 0, 0>>> while(i >= 0): ...     i += 1...     if(i > 10 and i < 20):...             continue......     sum += i;...     if(i == 100):...             print("End!!", sum)...             break...End!! 4915
```

#### 문제1\) 1부터 100까지의 합을 구하시오.

```python
i, sum = 0, 0while (i < 100):    i = i + 1    sum = sum + iprint(sum) #5050
```

```python
sum = 0 for i in range(100): # 0 ~ 99    sum = sum + (i + 1)print(sum) #5050
```

#### 문제2\) 1부터 100까지의 홀수의 합을 구하시오.

```python
i, sum = 0, 0while (i < 100):    i = i + 1    if (i % 2 == 1):        sum = sum + iprint(sum) #2500
```

```python
sum = 0 for i in range(100):     if (i % 2 == 1):        sum = sum + (i + 1)print(sum) #2550
```

#### 문제3\) 1 ~ 100 중에서 소수\(약수가 1과 자기자신\)의 합을구하시오.



