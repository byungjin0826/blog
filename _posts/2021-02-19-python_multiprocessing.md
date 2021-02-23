---
title: python 병렬처리와 ray에 대하여
tags: python, multiprocessing, multithread, ray
---

## python 병렬처리와 ray를 쓰는 이유.

병렬 처리는 멀티 스레드와 멀티 프로세싱의 두 가지 방법이 있다. 멀티 스레드는 프로세스를 여러 개의 조각(스레드)로 나누어 작업하는 방식이며, 멀티 프로세싱은 아예 여러 개의 프로세스로 동시에 처리하는 방식을 말한다. 두 가지의 장단점은 자원을 활용하는 방법의 차이에서 발생한다. 멀티 스레드는 stack 메모리를 제외한 다른 메모리를 공유한다. 따라서 성능은 좋지만 메모리 관리에 유의해야 한다. 잘못 사용하게 되면 경쟁 상태(race mode)라고 부르는 문제가 야기된다. 멀티 스레드로 성능 향상을 위해서는 멀티 코어가 필수적이다. 싱글 코어에서 스레드를 적용할 경우 순차처리와 성능차이가 없게 된다. 멀티 프로세싱은 자원을 개별적으로 사용하기에 안정적이나, 자원의 중복이나 비효율적인 측면이 있다.

파이썬에서는 GIL(Global Interpreter Lock)이라고 부르는 제약사항이 있다. GIL로 인하여 각 프로세스는 한 개의 CPU만이 사용가능하다. 위에 작성한 바와 같이 멀티 스레드는 멀티 코어 환경에서만 효과가 발휘된다. GIL로 인하여 CPU 작업이 주가 되는 경우 멀티스레드로 인한 성능 향상은 기대하기 어렵다. 다만 I/O 작업 같이 CPU의 사용이 적은 작업에는 효과적으로 적용할 수 있다. 따라서 파이썬에서는 병렬 처리를 활용하여 성능 향상을 하고자 할 경우, 멀티 프로세싱을 사용해야 한다.

파이썬에서 멀티 프로세싱은 `multiprocessing` 패키지를 활용하여 구현할 수 있다. 멀티 프로세싱은 작업 할당, 프로세스 간 데이터 교환 등 번거로운 작업을 동반한다. `ray` 패키지를 활용할 경우 간단한 방법으로 멀티 프로세싱을 구현할 수 있다. 또한 cpu 개수와 gpu 제한 등을 간단하게 처리할 수 있어, 딥러닝 프레임워크에 적용할 때도 유리한 점이 있다.

아래 작성한 코드와 같이 기존에 작성된 클래스에 `@ray.remote` 데코레이터를 추가하여 간단하게 변경 가능하다.

~~~python
import ray

ray.init(num_cpus=2, num_gpus=0.2)

@ray.remote
class Test:
  def __init__(self):
    self.n = 0
    print('init')
  
  def add():
    self.n += 1
    print('add')
    
  def get_n():
    print('get')
    return self.n
  
  
if __name__ == "__main__":
  actors = [Test.remote() for _ in range(5)]
  [a.add.remote for a in actors]
  object_ref = [a.get_n.remote() for a in actors]  # object ref를 반환
  results = ray.get(object_ref)
~~~

위에서 처리하는 방식에 대해서 간단하게 요약하자면 다음과 같다. ray는 프로세스를 액터의 수 만큼 생성하여 코드를 수행하고 object ref라고 하는 주소를 반환한다. 해당 결과물은 `ray.get` 을 통해 확인할 수 있다.

 프로세스 간 데이터 교환도  `ray.put` 을 이용할 수 있다.

~~~python
y = 1
object_ref = ray.put(y)
~~~

아래와 같이 메모리에 저장할 수 있고, 서로 다른 프로세스에서 해당 데이터를 활용할 수 있다.



### 요약

- 파이썬에서는 CPU의 사용이 적은 작업만 멀티스레드로 처리하자
- 멀티 프로세싱을 하고 싶다면 RAY 패키지를 활용하여 쉽게 처리할 수 있다



### 현재까지의 문제점

- worker 수를 무제한 늘릴 수는 없는 것 같다.
- elasticsearch를 통해 로드 시에 문제가 발생한다. -> ray.put 적용을 시도해 보는게 좋을 듯 하다.