# 2019-04-05-GoogleColab

## Colab에서 matplotlib 한글 폰트 사용하기

```text
# 그래프에서 한글 표현을 위해 폰트를 설치
%config InlineBackend.figure_format = 'retina'

!apt -qq -y install fonts-nanum > /dev/null

import matplotlib.font_manager as fm
fontpath = '/usr/share/fonts/truetype/nanum/NanumBarunGothic.ttf'
font = fm.FontProperties(fname=fontpath, size=9)

# 기본 글꼴 변경
import matplotlib as mpl
mpl.font_manager._rebuild()
mpl.pyplot.rc('font', family= 'NanumBarunGothic')
```

## Google Drive와 Colab 연동

```text
from google.colab import auth
auth.authenticate_user()

from google.colab import drive
drive.mount('/content/gdrive')

!cd content/gdrive/My Drive/Colab Notebooks/; ls -al; # 디렉터리 확인
```

