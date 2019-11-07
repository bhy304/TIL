---
description: Python Modules
---

# python09

## Standard Modules\(표준, 내부 모듈\)

* math, os, sys, datetime, time, random, urllib

## Module & Package

{% tabs %}
{% tab title="calcs.py" %}
```python
def plus(a, b):    return a + bdef minus(a, b):    return a - bdef mul(a, b):    return a * bdef div(a, b):    if b == 0:        return a     return a / b

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="moduletest.py" %}
```python
# from "파일명" import "function_name"from calcs import plus, minus, mul, divprint(plus(3, 5))import calcsprint(calcs.plus(3, 5))import sys, osprint("Path>>", sys.path)print("cwd>>", os.getcwd())os.chdir("..")print("cwd>>", os.getcwd())
```
{% endtab %}
{% endtabs %}

> dir\(sys\) : "sys" module이 어떤 변수와 메소드\(method\)를 가지고 있는지 확인!

### sys module

```bash
>>> import sys>>> sys.ps1'>>> '>>> sys.ps2'... '>>> sys.ps1 = "$python> "$python>
```

{% tabs %}
{% tab title="sys.py" %}
```python
import sysprint(sys.argv, len(sys.argv))if len(sys.argv) > 2:    sys.exit()with open(sys.argv[1],"r", encoding="utf8") as file:    for line in file:        print(line)
```
{% endtab %}
{% endtabs %}

```bash
python sys.py sys.py # cat sys.py 와 같음.
```

### os module

```bash
>>>import os>>>os.system('dir')bin   code  etc   lib    media  opt   root  sbin  sys  usrboot  dev   home  lib64  mnt    proc  run   srv   tmp  var0
```

```bash
>>> import os>>> os.name'posix'>>> os.getcwd()'/code'>>> os.chdir('..')>>> os.mkdir('hello')>>> os.system('dir')bin   code  etc    hi    lib    media  opt   root  sbin  sys  usrboot  dev   hello  home  lib64  mnt    proc  run   srv   tmp  var0>>> os.chdir('code')>>> os.system('dir')Dockerfile  docker-compose.yml  hello.py  hi  requirements.txt0>>> os.system('python hello.py')Hello, World!0>>> os.system('clear') # os.system('cls')0
```

### datetime module

```bash
>>> import datetime>>> now = datetime.datetime.now()>>> nowdatetime.datetime(2019, 6, 5, 3, 37, 57, 587442)>>> type(now)<class 'datetime.datetime'>>>> now.year2019>>> now.month6>>> now.hour3>>> now.minute37>>> now.second57# formatting>>> now.strftime('%Y-%m-%d %H:%M:%S')'2019-06-05 03:37:57'# *'년월일시분" : *로 string을 list로 만들어준다.(한 글자씩 {} 자리로 들어감)>>> now.strftime('%Y{} %m{} %d{} %H{} %M{}'.format(*"년월일시분"))'2019년 06월 05일 03시 37분'# timedelta : 특정 시각에 얼마만큼의 시간을 더하거나 빼는 역할>>> now + datetime.timedelta(weeks=1)datetime.datetime(2019, 6, 12, 3, 37, 57, 587442)>>> now.replace(year = (now.year + 1))datetime.datetime(2020, 6, 5, 3, 37, 57, 587442)
```

### time module

```bash
>>> import time>>> time.sleep(5); print("after 5 seconds!!")>>> time.time_ns() # 3.7버전에서만 가능1559706981841447000>>> st = time.time_ns()>>> time.time_ns() - st 10478850800>>> 10478850800 / 100000000010.4788508 # 약 10초 후(소요시간 확인할 수 있음)
```

### math module

```bash
>>> import math>>> math.floor(2.5)2>>> math.ceil(2.5)3>>> math.ceil(2.1)3>>> math.pi3.141592653589793>>> math.pow(2,3) #pow와 다른 점: 타입이 float8.0>>> pow(2,3) #파이썬내장함수8
```

### random module

```bash
>>> import random>>> print(random.randrange(6)) # 0~53>>> print(random.randrange(1,6))3>>> lst = [1,2,3,4,5]>>> random.shuffle(lst)>>> lst[1, 4, 2, 3, 5]>>> random.randint(1,7) # 1~75>>> fam_names = list("김이박최강고윤엄한배성백전황서천방지마피")>>> random.choice(fam_names)'이'>>> a = 0>>> b = 1>>> random.uniform(a, b) # a와 b 사이의 랜덤 실수0.9727629276812587>>> lst[5, 2, 3, 1, 4]>>> random.sample(lst, k=3) # 불특정 N개 추출[1, 4, 3]
```

### urllib module

```bash
>>> from urllib import request>>> url = "www.google.com">>> url'www.google.com'>>> html = request.urlopen(url).read()Traceback (most recent call last):  File "<stdin>", line 1, in <module>  File "/usr/local/lib/python3.6/urllib/request.py", line 223, in urlopen    return opener.open(url, data, timeout)  File "/usr/local/lib/python3.6/urllib/request.py", line 511, in open    req = Request(fullurl, data)  File "/usr/local/lib/python3.6/urllib/request.py", line 329, in __init__    self.full_url = url  File "/usr/local/lib/python3.6/urllib/request.py", line 355, in full_url    self._parse()  File "/usr/local/lib/python3.6/urllib/request.py", line 384, in _parse    raise ValueError("unknown url type: %r" % self.full_url)ValueError: unknown url type: 'www.google.com'
```

{% hint style="danger" %}
**SSL\(Secure Socket Layer\) 보안 인증서가** 없어서 에러 발생!!
{% endhint %}

```bash
from urllib import requestimport sslurl = "https://google.com"ctx = ssl.create_default_context()ctx.check_hostname = Falsectx.verify_mode = ssl.CERT_NONEhtml = urllib.request.urlopen(url, context=ctx).read()
```

### sys.path와 os.path의 차이

sys.path는 파이썬 라이브러리\(파이썬 시스템\)의 path이고, 

os.path는 operator system\(mac, windows 등/환경변수\)의 path이다.

```bash
import syssys.path
```

```bash
import osos.path
```

#### Try This!

1\) python 실행 전 화면 clear 하기를 os 모듈로 만들어보세요. 

2\) 현재 작업중인 hello 디렉토리에서 소스를 add, commit, push하기

