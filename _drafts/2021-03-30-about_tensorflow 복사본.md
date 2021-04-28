---
title: about TensorFlow
tags: TensorFlow
---

연구를 진행하며 막혔던 부분과 텐서플로우를 조금 더 잘활용하기 위해 알아야하는 부분들을 정리해보고자한다.



- graph와 session
- keras 활용 vs. 
- gpu 제어
- tensorflow architecture(XLA)
- tensorflow 1.x vs. 2.x



## graph와 session

텐서플로우는 연산그래프를 사용하는데, 노드와 꼭지점, 변으로 구성된다. 노드는 하나의 연산을 의미하며, 다른 노드로 전달할 값을 출력하는 역할을 한다. 연산그래프를 쓰는 이유는 의존관계를 이용하여 연산량을 최소화할 수 있기 때문인다.

`import tensorflow as tf`를 통해 tensorflow를 import하면 비어있는 기본 그래프가 만들어진다.

~~~~python
import tensorflow as tf


a = tf.constant(5)
b = tf.constant(2)
c = tf.constant(3)
~~~~



~~~python
d = tf.multiply(a, b)
e = tf.add(c, b)
f = tf.substract(d, e)
~~~



~~~python
sess = tf.Session()
outs = sess.run(f)
sess.close()
~~~



```python
import tensorflow as tf


g = tf.Graph()

tf.get_default_graph()

a = tf.constant(5)

a.graph is g
a.graph is tf.get_default_graph()
```



~~~python
import tensorflow as tf


g1 = tf.get_default_graph()
g2 = tf.Graph()


g2 is tf.get_default_graph()


with g2.as_default():
    g2 is tf.get_default_graph()
    
g2.get_default_graph()
~~~



~~~python
with tf.Session() as sess:
    fetches = [a, b, c, d, e, f]
    outs = sess.run(fetches)
~~~



