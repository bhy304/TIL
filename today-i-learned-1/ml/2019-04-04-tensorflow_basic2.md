# 2019-04-04-Tensorflow\_Basic2

## 텐서플로우의 특징

1\) 기본적으로 텐서를 활용한 그래프 수치 연산을 하는 도구 2\) 수학적인 의미에서의 그래프 : 노드와 엣지로 구성된 기하 모형 3\) 노드\(node\) : 연산 및 데이터를 정의하는 것 4\) 엣지\(edge\) : 노드들을 연결하는 것\(데이터의 흐름\) 5\) **텐서\(Tensor\) : 다차원 데이터 배열** 6\) **텐서플로 : 텐서가 노드에서 연산되고 엣지를 통해 돌아다닌다.**

## 텐서플로우의 기본 문법

1\) Session

* 그래프를 만드는 작업\(실행하는 것은 아님\)

  노드로 연산 및 데이터를 정의하고 코드 흐름으로 엣지를 구성함

* 그래프를 만든 이후 Session을 생성하여 실행을 시켜야 그래프의 시작점부터 모든 연산을 하게 되고

  동작을 하게 됨

* session을 실행시키면 엣지를 통해 데이터들이 출력됨
* 그래프를 만들고 \(모델링\) Session을 만들어 실행시켜야 노드가 엣지를 타고 이동하면서 원하는 형태로 코드가 동작됨

```python
  sess = tf.Session()
  sess.run(실행할 코드)
```

또는

```python
with tf.Session() as sess:
  sess.run(실행할 코드)
```

2\) Fetch : 코드에서 데이터값을 미리 정하는 것

* Feed : Placeholder 등을 통해 데이터값 없이 구조를 만들고 세션을 실행할 경우 feed\_dict을 통해 데이터를 전달
* placeholder : 노드에 들어갈 데이터의 형식을 미리 정해 놓는 형태

  ```python
  input = tf.placeholder(tf.float32)
  ```

  3\) 변수와 상수

* variable : 학습시키면서 최적화하는 변수의 용도로 사용됨 학습과정에서 지속적으로 바뀔 수 있는 중요한 값
* constant : 상수
* 변수의 선언

  ```python
  tf.Variable(초기값, 타입)
  ```

* 변수의 초기화

  ```python
  tf.global_variables_initializer()
  ```

  를 통해 초기화할 수 있음  
  변수는 반드시 초기화를 해야함  
  초기화는 노드에 값을 입력한다는 의미

* placeholder : 주로 입력 데이터를 활용하는 용도로 사용됨 feed\_dict을 통해 그래프에 데이터를 흐르게 하기 위한 용도

## 텐서플로 자료형의 종류

--생략--

[Next](https://github.com/bhy304/todayMarkdown/blob/master/2019-04-04-Tensorflow_Basic3.md)

