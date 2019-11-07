---
description: '자료구조 Set, 파이썬 내장함수(Built-in Functions) 1'
---

# python05

## Set 집합

{1, 2, 3},{4, 5, 6}

합집합\(\|\), 교집합\(&\), 차집합\(^\)

union\(\)

```bash
>>> s1 = {1,2,3}>>> s2 = {3,4,5}>>> s1 | s2{1, 2, 3, 4, 5}>>> s1 & s2{3}>>> s1 ^ s2{1, 2, 4, 5}>>> s1>>> s2>>> s1.union(s2)>>> ss = s1.union(s2)>>> s1.update(s2){1, 2, 3, 4, 5}
```

## Simple functions

> [https://docs.python.org/ko/3/library/functions.html](https://docs.python.org/ko/3/library/functions.html)

```bash
>>> abs(-3)3>>> divmod(5,2)(2, 1)# 진수 변환# bin() : 정수를 "0b" 가 앞에 붙은 이진 문자열로 변환>>> bin(7)'0b111'# oct() : 정수를 "0o"로 시작하는 8진수 문자열로 변환>>> oct(7)'0o7'# 정수를 "0x" 접두사가 붙은 소문자 16진수 문자열로 변환>>> hex(13)'0xd'>>> bool(0)False>>> bool('')False>>> bool()False>>> bool('abcd')True>>> bool(123)True>>> int('123')123>>> int(0.5)0>>> int(1.5)1>>> pow(2,3) # pow(x, y) : x 의 y 거듭제곱8>>> globals() # 현재 전역 심볼 테이블을 나타내는 딕셔너리를 돌려준다.>>> help(min) # 내장 도움말 시스템을 호출>>> type(s1)<class 'set'>
```

## Round

※ 거리가 같다면 짝수를 택함.

```bash
# round(2.5) vs round(2.51>>> round(1.5)2>>> round(2.5)2>>> round(2.51)3>>> round(2.3456, 3)2.346
```

## String functions

**format\(\), split\(\), len\(\), input\(\), print\(\), join\(\)**

```bash
>>> s = "abc">>> "-".join(list(s))'a-b-c'
```

## Class/Object functions

```bash
>>> dir()>>> import random>>> dir(random) # show the names in the random module(내장함수를 보여줌)>>> eval('print("123")') # string을 코드화시킴123>>> exec('print("123")')123
```

```python
class TestClass:    name = "TEST"    def __init__(self):        print("TTTTTTTTTTT")    @property    def full_name(self):        return self.name + " FFFFF"    @staticmethod    def static_method():        print("STATIC!!")    def get_name(self):        print("QQQQQQQQQQQQQQQ")        return self.name    def area(self, x, y):        return x * yclass Child(TestClass):    def get_name(self):        t = super().get_name()        return "Child Name:" + self.name    def area(self, x, y):        t = super().area(x, y)        return t / 2test = TestClass()child = Child()test.static_method()TestClass.static_method()cmd = input("Input the function name>> ")getattr(test, full_name)()getattr(TestClass, 'static_method')()# print("11111>>", test.get_name(), Child.get_name())# c = callable(test.get_name())# print("ccccc>>", c)
```

## **bytearray\(\), bytes\(\), chr\(\)**

bytearray\(s, 'encoding'\)

bytes\(s, 'encoding'\) \# read only bytearray

chr\(i\) \# chr\(97\) -&gt; 'a'

\*\*\*\*

