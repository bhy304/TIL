# 2019-04-04-Tensorflow\_Basic3

## Session1

```python
import tensorflow as tf
# 상수 선언
hello = tf.constant('Hellow World')
# 정의만 하고 실행이 되는 단계가 아니다.
print(hello) 
# 텐서플로우 자료형 정보만 출력된다. 
a = tf.constant(10)
b = tf.constant(32)
c = a+b #c = tf.add(a,b)와 같다
print(c) #객체만 만들었고 연산이 되는 단계는 아니다!

# 연산을 하려면 session을 생성해야한다.
sess = tf.Session()
print(sess.run(hello)) #세션.run()을 해야만 텐서 그래프(변수, 수식)을 실행할 수 있다!
print(str(sess.run(hello), encoding='utf-8'))
print(sess.run([a,b,c]))
# 세션 종료
sess.close()
```

## Session2

```python
import tensorflow as tf
node1 = tf.constant(3.0)
node2 = tf.constant(4.0)
node3 = tf.add(node1, node2)

with tf.Session() as sess:
  print("node3:", node3)
  print("sess.run(node3) : ", sess.run(node3))

# sess.run을 실행시키지 않으면 노드구조만 출력
# sess.run을 실행시켜야 실제 결과 출력
# with문을 쓰게 되면 세션을 생성된 후에 문장이 종료되면 자동으로 세션이 종료된다.
```

## Placeholder

```python
import tensorflow as tf
# Placeholder : 그래프의 입력 변수
input01 = tf.placeholder(tf.float32)
input02 = tf.placeholder(tf.float32)
output = tf.multiply(input01, input02)

with tf.Session() as sess:
  print(sess.run(output, feed_dict={input01: 3.0, input02: 5.0}))
  print(sess.run(output, feed_dict={input01: 0.0, input02: 6.0}))
  print(sess.run(output, feed_dict={input01: [2.0], input02: [6.0]}))  
# 같은 그래프 구조에 feed_dict={} 구문을 활용하여 데이터를 입력

# 텐서플로의 변수 선언
W = tf.Variable([.3], dtype=tf.float32)
b = tf.Variable([-.3], dtype=tf.float32)
x = tf.placeholder(tf.float32)
linear_model = tf.multiply(W, tf.add(x,b))

# 변수 초기화
init = tf.global_variable_initializer()

# 세션 시작
with tf.Session() as sess:
  sess.run(init)
  result = sess.run(linear_model, feed_dict={x:[1, 2, 3, 4]})

print(result, type(result))
```

```python
# x의 값에 따라 linear_model 계산
# 결과를 numpy.ndarray로 리턴
x = tf.placeholder(tf.float32)
linear_model = tf.multiply(W, tf.add(x,b))
init = tf.global_variable_initializer()
with tf.Session() as sess:
  sess.run(init)
  result = sess.run(linear_model, feed_dict={[1,2,3,4]})

print(result, type(result))
```

## placeholder와 변수의 개념

```python
import tensorflow as tf
# tf.placeholder : 계산을 실행할 때 입력값을 받는 변수
# None : 크기가 정해지지 않았음을 의미, 그래프가 더 늘어날 수 있기 때문에...?
X = tf.placeholder(tf.float32, [None, 3])
print(X)
# X 플레이스홀더에 넣을 값
# 두번째 차원의 요소의 갯수는 3개

x_data = [[1,2,3],[4,5,6]] # 2행 3열

# tf.Variable() : 그래프를 계산하면서 최적화할 변수
# tf.random_normal() : 각 변수들의 초기값을 정규분포 랜덤값으로 초기화
W = tf.Variable(tf.random_normal([3, 2]))
b = tf.Variable(tf.random_normal([2, 1]))

# 입력값과 변수들을 계산할 수식 작성
# tf.matmul 처럼 mat으로 시작하는 함수로 행렬 계산 수행
# 행렬 곱셈
expr = tf.matmul(X, W) + b
sess = tf.Session()

# 변수 초기화
sess.run(tf.global_variables_initializer())
print(x_data)
print(sess.run(W))
print(sess.run(b))

# 수식에 값을 전달하는 방법
# 세션.run(수식, feed_dict={변수: 값})
print(sess.run(expr, feed_dict={X: x_data})

# 세션 종료
sess.close()
```

[Next](https://github.com/bhy304/todayMarkdown/blob/master/2019-04-04-Tensorflow_Basic4.md)

