# 2019-04-03-MachineLearning1

[1.Reference site](https://forensics.tistory.com/4)  
[2.동영상 강의](https://www.youtube.com/watch?v=qPMeuL2LIqY&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm&index=2)

## 기본적인 머신러닝의 용어와 개념 설명

**1. What is ML\(Machine Learning\)?**

머신러닝은 무엇인가?  
**머신러닝은 일종의 소프트웨어\(프로그램\)으로 명시적인 프로그램\(Explicit Program\)** 이다.  
대부분의 소프트웨어는 사용자의 입력에 따라 데이터를 보여주게 된다.

명시적인 프로그램\(Explicit Program\)이란 개발자\(사람\)가 입력 조건과 프로그램 상태 조건에 따라 프로그램이 동작하는 방식을 모두 구현하는 프로그램 방식이다. 굉장히 훌륭한 프로그램이 많지만, 어떤 부분에서는 정확하게 프로그래밍하기 어려운 경우가 있다. 많이 사용하는 스팸 필터, 자율주행자동차가 그 예이다. 스팸 필터, 자율주행자동차는 모두 많은 규칙을 필요로 한다는 단점이 있다.

1959년 "Arthur Samuel"이 일일이 프로그래밍하지 않고 어떤 자료\(현상\)에서 자동적으로 학습하면 어떨까? 하는 생각을 했고, 이것이 바로 머신러닝이라 할 수 있다. 프로그램인데 개발자가 일일이 어떻게 하는지를 정하지 않고 프로그램 자체가 어떤 데이터를 보고 학습해서 뭔가를 배우는 능력을 갖는 프로그램을 머신러닝이라 할 수 있다.

**2. What is learning?**

기계학습 프로그램은 학습을 해야하기 때문에 학습에 필요한 데이터를 미리 제공해야 한다.  
학습 방법에는 다음과 같은 2가지로 분류한다.

**2-1. Supervised learning : 지도학습**

* 정해져 있는 데이터\(Training set\), label이 정해져 있는 데이터를 가지고 학습한다.
* 지도학습의 예로 주어진 이미지를 학습시키고 고양이인지 개인지 구별하는 프로그램을 들 수 있따.
* 일반적인 지도 학습의 문제
  * Image labeling
  * Email spam filter
  * Predicting exam score
* Training data set 기계학습 프로그램에 표시된 데이터\(labeled data\)로 학습을 시키면 어떤 모델이 만들어진다. 이렇게 학습된 모델에 학습되지 않은 데이터를 주고 결과값을 얻을 수 있다.
  * AlphaGo 로 Training data set으로 학습한 지도학습의 예라고 할 수 있다. 
* 지도 학습도 결과에 따라 분류할 수 있다.
  * Predicting final exam score based on time spent : **Regression\(회귀\)**
  * Pass/non-pass based on time spent : **binary classification\(이진 분류\)**
  * Letter grade\(A,B,C,E and F\) based on time spent : **multi-label classification\(다중 분류\)**

**2-2. Unsupervised learning : 비지도학습\(un-labeled data\)**

* 어떤 데이터의 경우에는 우리가 일일이 어떤 label을 줄 수 없는 경우가 있다. 프로그램이 데이터를 보고 스스로 학습!
* 자동적으로 유사한 뉴스를 모으는 Google news grouping 
* 비슷한 단어를 모으는 Word clustering 

