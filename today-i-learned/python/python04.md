# python04

{% tabs %}
{% tab title="rect.py" %}
```python
# string -> int
def to_int(s):
    if type(s) == str:
        return int(s)
    else:
        return s

class 사각형:
    x, y = 0, 0
    def __init__(self):
        print('사각형 created')

# 사각형 상속
class 직사각형(사각형):
    def 넓이(self, x, y):
        return to_int(x) * to_int(y)

class 평행사변형(사각형):
    def 넓이(self, x, y):
        return to_int(x) * to_int(y)

# 직사각형과 평행사변형의 넓이 구하기
while True:
    print()
    rect_type = input("사각형의 종류는?\n 1)직사각형\n 2)평행사변형\n (quit:q)>> ")

    if (rect_type == 'q'):
        break 

    if rect_type == '1':
        rect1 = 직사각형()
        가로_세로 = input("가로와 세로는??(usage:가로,세로)")
        print("111>>", 가로_세로, 가로_세로.split(','))
        가로, 세로 = 가로_세로.split(',')
        # rect1.넓이(가로, 세로)
        # 직사각형.넓이(가로, 세로)
        print("222>>", 가로, 세로)
        결과 = rect1.넓이(가로, 세로)
        print("직사각형의 넓이는 {}입니다.".format(결과))
    else:
        rect2 = 평행사변형()
        밑변_높이 = input("밑변과 높이는??(usage:밑변, 높이)")
        밑변, 높이 = 밑변_높이.split(',')
        결과 = rect2.넓이(밑변, 높이)
        print("평행사변형의 넓이는 {}입니다.".format(결과))
```
{% endtab %}
{% endtabs %}

## Code refactoring

> **리팩터링**\(refactoring\)은 [소프트웨어 공학](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B3%B5%ED%95%99)에서 '**결과의 변경 없이 코드의 구조를 재조정함**'을 뜻한다. **주로 가독성을 높이고 유지보수를 편하게 한다.** 버그를 없애거나 새로운 기능을 추가하는 행위는 아니다. 사용자가 보는 외부 화면은 그대로 두면서 내부 논리나 구조를 바꾸고 개선하는 유지보수 행위이다.

{% tabs %}
{% tab title="rect2.py" %}
```python
class Casting:
    def to_int(s):
        if type(s) == str:
            return int(s.strip())
        else:
            return s

class 사각형:
    name = "사각형"
    msg = "가로와 세로는??(usage:가로,세로) >"

    def __init__(self):
        print('사각형 created')

    def input_data(self):
        datum = input(self.msg) # 5,3
        data = datum.split(',') # ['5', '3']
        x = Casting.to_int(data[0])
        if len(data) < 2:
            y = x
        else:
            y = Casting.to_int(data[1])
        self.__새넓이(x,y)

    def __새넓이(self, x, y): #은닉화
        r = x * y 
        print("{}의 넓이는 {}입니다.".format(self.name, r))

class 직사각형(사각형):
    name = "직사각형"
    msg = "가로와 세로는??(usage:가로,세로) > "

class 평행사변형(사각형):
    name = "평행사변형"
    msg = "밑변과 높이는??(usage:밑변, 높이) > "

class 정사각형(사각형):
    name = "정사각형"
    msg = "한 변의 길이는??(usage:길이) > "

all_rects = [사각형(), 직사각형(), 평행사변형(), 정사각형()]

first_msg = '사각형의 종류는?\n'
for i, r in enumerate(all_rects):
    if i == 0:
        continue
    first_msg += "{:d}) {} \n".format(i, r.name)

first_msg += "(quit:q) >>"

while True:
    print("\n ------------------------------")
    rect_type = input(first_msg)

    if (rect_type == 'q'):
        break 

    rect_index = Casting.to_int(rect_type)
    if rect_index > len(all_rects):
        rect_index = 0

    rect = all_rects[rect_index]
    rect.input_data()
```
{% endtab %}
{% endtabs %}