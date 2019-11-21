# 2019-04-04-Tensorflow\_Basic1

## 텐서플로우 기초 문법

### 머신러닝/인공지능

1\) 인간이 코딩 등으로 사전에 정의내린 행동이 아닌 행동을 하도록 하는 것에 가까운 개념\(Arthur Samuel, 1959\) <br>
2\) 스팸필터, 상품추천, 자율주행차 등의 다양한 분야에서 활용되고 있다. <br>
3\) 머신러닝은 러닝, 즉 "학습"의 개념이 포함되어 있다. <br>

### 학습

머신러닝을 코딩한다는 것은 결국 "학습"하는 방법을 코딩한다는 것  
어떻게 학습을 시킬 것인가 = 어떻게 시행착오를 거치게 할 것인가?

1\) 어떤 목표를 정해 놓고 목표를 달성하게 할 경우 의도된 결과를 도출하도록 하는 것 <br>
2\) 손실 함수, 비용함수\(cost function, loss function\) :  
학습을 통해 그 값을 최소로 만드는 것을 목표로 하는 함수

## Supervised vs. Unsupervised

1\) 지도학습\(Supervised learning\)

* 학습 데이터에 답\(labeled data\)이 함께 제공
* 고양이 그림에 고양이라고 표시해 주는 것
* 대부분의 머신러닝 알고리즘이 해당됨

2\) 비지도학습\(Unsupervised learning\)

* 학습데이터에 답이 없음\(unlabeled data\)
* 미리 답을 줄 수 없는 데이터
* 일부 머신러닝기법에서 사용

### 예측과 분류\(Prediction/Regression, Classification\)

1\) 예측\(Prediction, Regression\) 답을 알고 있는 데이터로 학습을 시킨 후 새로운 데이터가 들어왔을 때 가장 유사한 결과값을 예상하도록 하는 것 <br>
2\) 분류\(Classification\) 레이블이 있는 데이터로 분류하는 것을 학습시킨 후 레이블이 없는 새로운 데이터가 들어왔을 때 레이블을 부여하는 것

### 딥러닝\(Deep Learning\)

1\) 인공신경망에 기반하여 설계된 개념 <br>
2\) 1989년 얀 르쿤의 연구팀에 의해 제안된 알고리즘 우편물에 손으로 쓰여진 우편번호를 인식하는 심층 신경망\(Deep Neural Network\)을 소개함. <br>
3\) 최근 하드웨어의 발전에 힘입어 다시 주목을 받게 됨 <br>
4\) 은닉층이 1개인 단순한 인공신경망과 달리 다수의 은닉층을 사용함 <br>

### 케라스\(Keras\)

1\) 파이썬으로 개발된 오픈 소스 신경망 라이브러리 <br>
2\) Deeplearning4j, 텐서플로 등의 기존 딥러닝 라이브러리를 기반으로 더 직관적이고 간결한 코드로 빠른 실험이 가능하도록 구현됨

### 텐서플로우 [Tensorflow](https://www.tensorflow.org/)

1\) 구글에서 만든 오픈소스 머신러닝 프레임웍 <br>
2\) 다양한 언어를 제공하며 파이썬이 가장 많이 사용됨

---
## Reference
[LifeSoft\_Youtube\_lecture](https://www.youtube.com/watch?v=jkG2qjCScss&list=PLY9pe3iUjRrT6wZTIA5YriQxvfXf-yxhF&index=38)