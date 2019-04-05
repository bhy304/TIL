# Colab에서 matplotlib 한글 폰트 사용하기

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
