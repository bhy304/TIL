# 2019-04-03-MachinLearning2

[동영상 강의](https://www.youtube.com/watch?v=Hax03rCn3UI&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm&index=4)

## Linear Regression의 개념

어떤 학생이 몇 시간 정도 공부를 했더니 얼마 정도의 성적이 나왔다는 데이터를 가지고 Supervised Learning을 한다고 가정을 해보자!

### Predicting exam score: regression

| **x\(hours\)** | **y\(score\)** |
| :--- | :--- |
| 10 | 90 |
| 9 | 80 |
| 3 | 50 |
| 2 | 30 |

* x : 예측을 하기 위한 기본적인 자료
* y : 예측하려는 값
* regression : 0~100 사이의 값을 예측하는 것
* training : 데이터로 학습을 시키는 것
* 학습이 끝나면 모델이 만들어진다.
* regression을 사용한다는 것은 어떤 학생이 7시간 공부를 했는 데 \(시험을 치기 전에\) 몇 점을 맞을 수 있을지 인공지능에게 물어본다. 그럼 인공지능은 regression을 사용해 점수를 예측해준다!

### Linear Regression 모델은 어떻게 동작하는가?

**Regression\(training data\)**

| **x** | **y** |
| :--- | :--- |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |

regression 모델을 학습한다는 것은 하나의 가설\(Hypothesis\)을 세울 필요가 있다.

* \(Linear\) Hypothesis

  > H\(x\) = Wx + b

  * H\(x\) : 가설, 예측값
  * W : weight
  * b : bias
  * W와 b에 따라 여러 가지 직선이 만들어질 수 있다. 

* Cost\(Loss\) funciton : 거리를 측정하는 함수 우리가 세운 가설과 실제 데이터가 얼마나 다른가를 나타낸다.

  > \(H\(x\)-y\)²

* Goal : Minimize Cost Cost 값을 최소화하는 W와 b를 구하자!

