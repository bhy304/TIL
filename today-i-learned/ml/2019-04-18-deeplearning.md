# 2019-04-18-DeepLearning

## 딥러닝 자연어 처리

### Bag of Words

* Bag of words는 문자를 숫자로 표현하는 방법 중 하나
* 단어의 출현 빈도를 수치로 표현한 값을 통해 문장의 유사도를 알 수 있다. 
* 머신러닝 모델의 입력값\(Input data\)로 활용할 수 있다.
* Bag of words의 단점 
  
  1\) Sparsity : 머신러닝 모델을 학습할 때 계산량이 상당히 높아지고 메모리 또한 단어많이 사용된다. <br>
  2\) Frequent word has more power : 많이 출현한 단어가 힘이 쎄진다. <br>
  3\) Ignoring word orders : 단어의 순서를 철저히 무시\(문맥을 무시하게 된다.\) <br> 
  4\) Out of vocabulary : 보지 못한 단어들은 처리를 못한다. 예\) 오타, 줄임말 등

### N-gram

* 연속적으로 N개의 token으로 구성된 것
* token은 자연어 처리에서 보통 word, character를 의미함
* Bag of words의 단점\(단어의 순서를 무시\)을 극복

  1\) 1-gram\(unigram\) <br>
  2\) 2-gram\(bigram\) <br>
  3\) 3-gram\(trigram\) <br>

### TF-IDF

* What is TF-IDF?   **Term Frequency \* Inverse Document Frequency**
* Why TF-IDF? 어떤 한 문서가 주어졌을 때 문서는 단어로 구성됨. 각 단어별 연관성을 알고 싶을 때 TF-IDF를 사용하고 TF-IDF는 수치로 된 값이다.
  * 단어의 문서 연관성이란?   

```text
어떤 문장이 있을 때 각 문장은 단어로 구성됨.   


각 단어별로 문서에 대한 정보를 얼마만큼 가지고 있는 지를 수치로 나타낸 값이다.
```

* What is Term Frequency? 
  
  TF\(단어 빈도, term frequency\)는 특정한 단어가 문서 내에 얼마나 자주 등장하는지를 나타내는 값으로, 이 값이 높을 수록 문서에서 중요하다고 생각할 수 있다.

  문서가 있을 때 단어가 여러 번 출현했다면 여러 번 출현한 만큼 연관성이 높을 것이다라는 가설 안에 TF Score를 사용한다.

  하지만 단어 자체가 문서군 내에서 자주 사용되는 경우, 이것은 그 단어가 흔하게 등장한다는 것을 의미한다.

  연관성은 없음에도 불구하고 여러 문장에 자주 출현하는 단어들이 있기 때문에 TF Score만으로는 단어의 문서 연관성을 나타내기엔 부족하다.

* What is IDF? 
  
  DF\(문서 빈도, document frequency\), TF 값의 역수를 IDF\(역문서 빈도, inverse document frequency\)라고 한다.

* IDF 공식 : 
  Log\(Total \# of Docs / \# of Docs with the term in it\)

  **TF-IDF는 문서가 주어졌을 때 또는 문장이 주어졌을 때 각 단어별로 그 문장의 연성을 수치로 나타낸 값**

### Word2Vec

Deep learning 모델에 **text**를 넣을 수 있을까? **NO**  
Deep learning 모델에 **number**를 넣을 수 있을까? **YES**

* What is **Encoding**?   **Convert Text to Number**
* What is **One Hot Encoding**?  
  **Convert Text to Vector**

  하지만! One Hot Encoding은 유사도\(Similarity\)가 없다.

  1.distance가 가까우면 비슷하다고 판단되지만 one hot encoding을 사용하면 각각의 데이터가 거리가 같아져버린다.  
  2.두 개의 데이터 포인트 간의 각도가 전부다 90도가 나온다. 즉, 다 0이 되버리므로 유사도를 발견할 수가 없다.

이러한 문제때문에 Embedding을 알아야한다.

**Embedding**  
Encoding 대신에 Embedding을 사용함으로써 단어 Vector끼리의 유사도를 구할 수가 있다.

Embedding은 one hot encoding보다 저차원이고 유사도를 가진다.

즉, 고차원의 데이터를 그보다 낮은 차원으로 변환하면서 모든 데이터간의 관계가 성립하도록 처리하는 과정이다.

**Word2Vec**  
Word2Vec은 Embedding 중 하나  
유사도는 비슷한 위치에 있는 단어들\(Neighbor words\) 사이에서 얻게 된다.

### RNN

### 시퀀스투시퀀스

---
## Reference
[딥러닝 자연어처리](https://www.youtube.com/watch?v=dKYFfUtij_U&list=PLVNY1HnUlO26qqZznHVWAqjS1fWw0zqnT&index=1)