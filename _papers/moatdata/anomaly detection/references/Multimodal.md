# Anomaly Detection and Interpretation using Multimodal Autoencoder and Sparse Optimization

- abstarct

자동화된 이상탐지는 관리자의 부담을 줄이고 서비스를 신뢰성있게 유지하기 위해 ICT 시스템을 관리하기 위해 필수적이다. 다양하고 지속적으로 발생하는 이상을 감지하기위해 ... 딥러닝 기반의 이상탐지는 그러므로 이러한 복잡성을 고려해야한다. 인풋 데이터의 디멘젼이 ...

## 1. Introduction

이상 진단과 복구는 필수다. 가상화, 클라우드 서버 등을 포함하여 ICT 시스템의 성장에도 불구하고, 시스템 장애의 유형은 증가하였다. 따라서 관리자의 부담도 커졌다. 이상을 자동으로 감지하는 것은 관리자의 업무량을 감소시켜줄 뿐 아니라 서비스 품질에도 영향을 준다. 다양한 ..

그러나 ICT system에서 cross-domain의 데이터는 관계가 복잡하다. MIB data, 와 네트워크.... 등등. 예를 들어 control과 data planes 사이의 동기화 실패는 네트워크에서 많은 종류의 장애를 발생시킬수 있고 유지보수 되어야 한다. 불변은 crose-domaindp Ekfk ekfmsrjtdmfh qhdlsek. 

네트워크 관리 시스템에서 



## 2. Related Work

MIND는 분산 네트워크에 대한 것이며, 이상 트래픽 패턴을 감지할 수 있다. Sketches와 PCA는 차원축소를 이용한 알고리즘이다. 시스템 모니터에 대한 이상탐지 성능도 논의 되었다. I/O system 성능과 관련하여 전조를 분석한 것도 있다.



## 3. Autoencoder

## 4. Algorithm for estimating contributing dimensions





## 5. Multimodal autoencoder

![image-20210317165257790](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210317165257790.png)

ICT systems로부터 수집된 크로스 도메인 데이터는 분석 되어져야한다. 여러가지의 이상을 탐지해야된다. 이상은 크로스 도메인의 관계 붕계로 보여진다. 그러나 크로스 도메인을 위해 AE를 만드는 것에 두 가지 큰 문제가 있다.

(1) 어떤 메트릭에서는 크로스 도메인 관계가 있어보이지만, 많은 메트릭은 관계가 없어보인다. 그러므로, 정상 상태의 사이즈가 커져야 한다. 모니터된 메트릭의 숫자만큼 증가 시켜야한다. 그러나 학습 데이터의 크기는 제한이 있고 정상 상태를 학습하기에 충분하지 않다.

(2) 데이터의 학습가능성은 데이터에 종류에 따라 다르고, 통합적인 분석을 위해 고려되야 한다. 두 종류의 데이터가 하나의 AE로 학습 된다면 ...

이러한 문제들을 해결하기 위하여 멀티모달 오토인코더를 제안한다. 





## 6. Evaluation

### 6.1 Simulated Data

### 6.2 Benchmark Data

- NSL-KDD
- 



## 7. Use case with real measured data

### 7.1 Data Description

### 7.2 Future Extraction

### 7.3 Evaluation Method

### 7.4 Evaluation Results

## 8. Conclusion



# Deep Coupling Autoencoder for Fault Diagnosis with Multimodal Sensory Data

- abstract

