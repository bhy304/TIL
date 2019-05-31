---
description: 'Input, Function 함수, Class'
---

# python03

```python
lst = ['오렌지','사과','배']
dic = {'오렌지':400,'사과':200,'바나나':300}

for key in dic:
    print("key=", key, dic[key]) #dic['key']

print(list(enumerate(lst)))
#[(0, '오렌지'), (1, '사과'), (2, '배')]

for i, value in enumerate(lst):
    print("tt=", i, value)
    print(lst[i])

for key, element in dic.items():
    print("items.key=", key, ", elements=", element)

for i in range(0, 20, 2):
    print(i)

arr = [i ** 2 for i in range(0, 20, 2)]
print(arr)

lst = []
for i in range(0, 20, 2):
    print(i)
    i = i ** 2
    lst.append(i)

print("최소값:", min(arr))
print("최대값:", max(arr))

lst = ['사과','배']
outs = [f for f in lst if f != '사과']
print(outs)
```

## **I**nput

input value is **String Type**

```python
cmd = input("Input>>>")
print(cmd)

cmds = cmd.split(',')
print(cmds)
```

#### Try this

이름, 나이, 성별을 입력받아, "당신의 이름은 {}, 나이는 {}, 성별은 {} 입니다." 출력

```python
cmd = input("이름, 나이, 성별을 입력하시오>> ")
cmds= cmd.split(',')
name, age, gender = cmds[0],cmds[1], cmds[2]

print("당신의 이름은 {}, 나이는 {}, 성별은 {} 입니다.".format(name, age, gender))
```

```bash
cmd = input("Input(usage: 이름,나이,성별)>> ")
print("aaa=" + cmd + '.')

error_msg = "정확히 입력해주세요!!!"

# 1. 값 존재 여부 체크
if cmd == '':
    print(error_msg)
    exit()
  
# 2. , 가 있는지 체크
# if ',' not in cmd:
if cmd.find(',') == -1:
    print(error_msg)
    exit()

isExistComma = False
for i in cmd:
    if i == ',':
        isExistComma = True
        break

# if !isExistComma
if isExistComma == False:
    print(error_msg)
    exit()


cmds = cmd.split(',')
# 3. 2개의 값이 있는지!
if len(cmds) != 3:
    print(error_msg)
    exit()

outmsg = "당신의 이름은 {}, 나이는 {}, 성별은 {}입니다."
print(outmsg.format(cmds[0],cmds[1],cmds[2]))
```

## Function \(Method,함수\)

```python
def fn():
    print("fn called")

def exp(x):
    return x ** 2

exp3 = exp(3)
print(exp3)
print(exp(9))

def get_fruits():
    return ['오렌지','사과','바나나']

print(get_fruits()[1])
```

```python
def get_name():
    return 'Kent','Beck'

def full_name(first_name, last_name):
    return first_name + ' ' + last_name

name = get_name()
# name[1] = "aaaa" # Tuple은 Read Only List이기 때문에 변경할 수 없음!
print(name, full_name('Steave','Loser')) 
```

```python
# * : 가변인자(valuable param) => Tuple 타입
def var_param(a, *vp):
    print(type(vp))
    print(a, len(vp), vp[len(vp) -1])
var_param('aa','bb','cc')
```

```python
def default_param(a, b='BB'):
    print(a, b)
default_param('aa')
default_param('aa','bbbbbbbbbbb')
```

#### Try this

두 수를 받아, 사칙연산\(+,-,\*,/\)을 수행하는 함수를 만들어 보시오.

```python
def plus(a, b):
    return a + b
    
def minus(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return a
    return a / b

cmd = input("수식을 입력하세요(usage: 2 + 3)> ")
cmds = cmd.split(' ')

# @Try cmds 하나만으로 set해보기!
a, op, b = cmds
# print("a=", a, ", op =", op, ", b=", b)
a, b = int(a), int(b)

#a, op, b = int(cmds[0]), cmds[1], int(cmds[2])

if op == '+':
    r = plus(a, b)

elif op == '-':
    r = minus(a, b)

elif op == '*':
    r = multiply(a, b)

else:
    r = divide(a,b)

if op in '+-*':
    print("Answer is {:d}".format(r))
else:
    print("Answer is {:.2f}".format(r))
```

## Class



