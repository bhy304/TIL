---
description: Local Variables vs Global Variables
---

# python08

## Local Variables vs Global Variables

### GC\(Garbage Collector\)

* object가 서로 연결이 끊어지거나 불필요시 메모리에서 해제\(Release\)

### Local Variable\(지역 변수\)

* **블록 내에서 유효**
* 블록을 벗어나면 메모리에서 해제됨\(GC\)

### Global Variable\(전역 변수\)

* **한 개의 파일 전체에서 사용**되는 변수
* 프로그램 종료될 때까지 메모리에 유지\(유효\)

## Global Variables in Python

Block 내에서 **global** keyword가 없을 시 Local Variable이 된다.\(별도의 메모리 공간에 위치\)

```python
g_x = 1000 # 전역변수

def change_x():
    #g_x = 300 # 지역변수
    global g_x # global 선언해주면 g_x는 전역변수와 같아지게 됨.
    g_x = 300
    print("inner def>>", g_x)
    
change_x()
print("222>>", g_x)
```

