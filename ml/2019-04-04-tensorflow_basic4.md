# 2019-04-04-Tensorflow\_Basic4

◆ Reference : [LifeSoft\_Youtube\_lecture](https://www.youtube.com/watch?v=pnSP5hPGyI0&list=PLY9pe3iUjRrT6wZTIA5YriQxvfXf-yxhF&index=39)

## TensorFlow 실습

### Tensorflow 주요 개념

**1\) 오퍼레이션\(Operation\)**

* 그래프 상의 노드
* 하나 이상의 텐서를 받을 수 있음
* 계산을 수행하고 결과를 하나 이상의 텐서로 리턴

**2\) 텐서\(Tensor\)**

* 일종의 다차원 배열
* 내부적으로 모든 데이터는 텐서를 통해 표현됨
* 그래프 내의 오퍼레이션 간에는 텐서만이 전달됨

**3\) 세션\(Session\)**

* 그래프를 실행하기 위해서 필요한 객체

**4\) 변수\(Variables\)**

* 그래프 실행시 파라미터를 저장하고 갱신하는 데 사용됨
* 메모리 상에서 텐서를 저장하는 버퍼 역할

### 실습 예제

-- Google Colab에서 실습 실행 --

