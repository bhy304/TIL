---
description: 외부 모듈
---

# python10

## pip : 외부 모듈 설치

Usage: pip  &lt;command&gt; \[options\]

```bash
pip list
pip install #<모듈명>
pip uninstall
python -m site # sys.path처럼 파이썬라이브러리가 설치되어 있는 디렉터리 확인
```

## BeautifulSoup4

**HTML 및 XML 파일에서 원하는 데이터를 손쉽게 Parsing 할 수 있는 Python 라이브러리**

{% embed url="https://www.crummy.com/software/BeautifulSoup/" %}

```bash
pip install beautifulsoup4
pip install requests
# 설치 확인
pip show beautifulsoup4
from bs4 import BeautifulSoup
```

## HTTP

 HTTP 메시지는 서버와 클라이언트 간에 데이터가 교환되는 방식입니다. 메시지 타입은 두 가지가 있습니다. **요청\(**_**request\)은**_ **클라이언트가 서버로 전달해서 서버의 액션이 일어나게끔 하는 메시지**고, **응답\(**_**response\)은 요청**_**에 대한 서버의 답변**입니다.

* **request**
* **response**
* header\(user-agent, referer\)
* cookie
* session
* method\(get, post, put, patch, delete, options\)
* statuscode

## requests module

```python
import requests
r = requests.get('http://www.google.com', timeout=(5 ,14))
r.text
r.status_code
```



