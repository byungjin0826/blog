# Time series anomaly detection

- Abstract

구글은 사용자들에게 정확한 결과를 전달하기 위해 산업 파트너들로부터 얻은 지속적인 스트림 데이터를 사용한다. 갑작스런 트래픽의 저하는 이슈의 발생의 지표가 될 수 있으며, 치료 행위가 필요하다는 것을 조기에 알려줄 수 있다. 이러한 저하를 감지하는 것이 중요한 이유는 스트림은 다양하고 주기적으로 치솟는 노이즈가 섞여 있다. 우리는 이러한 스트림 데이터에서 이상을 예측 할 수 있는 지에 대하여 조사하였다. 우리의 목표는 기계학습과 통계적인 방법을 활용하여 주기적이거나 노이즈, 트래픽 패턴 등을 제거하고 이상 저하를 분류하는 것이다. 우리는  지도학습에 바로 사용할 수 있는 많은 양의 분류된 데이터를 가지고 있지 못하기 떄문에 두가지 방법을 사용하여 문제에 접근하기로 하였다. 첫번째는 시계열 데이터의 값을 예측하기 위하여 DNN, RNN, LSTM 등의 모델들을 학습하는 것이다. 두번째는 실제 값과 예측값을 비교하여 이상을 탐지하는 룰을 만드는 것이다. 문제를 해결하기 위해서는 짧은 기간동안에 발생하는 이상보다는 지속적인 이상을 찾는 것이 중요하기 때문에 우리의 두가지 이상탐지 방법은 단일 포인트 보다는 지속적인 섹션의 데이터를 포착하는 것을 목표로 한다. 우리는 여러개의 모델을 조합하는 것을 시도하였으며, 조합하는 것이 이상을 탐지하는 것에 효과적임을 증명하였다. 



## 1. Introduction

### A. About the data

5분 간격으로 저장된 14개의 다른 데이터 셋을 조사하였다. 이것은 한시간마다 12개의 데이터가 발생하며 하루에는 288개가 발생됨을 의미한다. 우리의 목표는 일상적인 트래픽 폭주의 부재와 같은 이상을 탐지하는 것이 목표이다. 지속적으로 낮거나 심지어 0이 되는 값들은 제외하면서. unix timestamp와 bytes per second, 오직 두가지 데이터만 사용하였다.

이 데이터에는 정확하게 마킹된 이상은 없음에도 불구하고 이상이 없음을 의미하지는 않았다.  프로젝트 초기에는 정보를 알고 있지 못하였다.

### B. About the problem



## 4. Detection rules

우리는 accumulaotr method와 gaussian tail probability method에 대하여 조사하였다. 우리의 실험을 통해서 이상탐지 규칙이 효과적이라는 것을 알았다. 그러므로 우리는 두가지를 조합하여 하이브리드 모델을 쓰는 것이 효과적이라는 것을 발견하였다. 

### A. Accumulator

accumulator 규칙의 목표는 지속적인 이상이 나타나기 전에 짧은 이상들이 여러번 발생하는 것을 찾는 것이다. 우리는 두가지 다른 룰을 시도하였다. 어떻게 이상을 탐지할 것인지? accumulator 규칙의 일부분으로 시험할 것인지? 이 규칙은 point anomaly가 발생할 경우 증가하고, 예측값이 정확하면 감소하는 카운터를 포함한다. 이것의 목표는 noise를 방지하는 것이다.

#### 1) Threshold

이 알고리즘은 local anomaly를 정의한다. local anomaly는 실제 값이 예상한 값보다 큰지 작은지를 비교한다.



#### 2) Variance based

예측한 20개의 데이터에 대한 rolling variance를 계산한다. 노이즈가 많은 영역에서는 더 많은 노이즈를 허용한다. 그러나 이러한 방법은 simple threshold보다는 효과가 떨어지는 것으로 보인다.



### B. Gaussian Tail Probability

Numenta's Rule 

추론 값과 정답을 비교하여 anomaly score를 우선 계산해야한다. 

#### 

## 5. Prediction models

### A. Hyperparameters

### B. Baseline (Threshold model)

### C. Fourier Series

### D. Deep Neural Network (DNN)

### E. Recurrent Neural Networ (RNN)

### F. LSTM





# Anomaly detection in Multivariate Non-stationary Time Series for Automatic DBMS Diagnosis

- Abstarct

dbms에서 이상탐지는 매우 중요하다. 빅데이터 시스템에서 통계와 이벤트 지표가 증가했기 때문이다. 본 논문에서는 자동 DBMS 진단 시스템을 제안할 것이다. 이 시스템은 특정 기간에 대해서 이상이 발생한 지표와 원인 이벤트를 찾을 것이다. deep autoencoder로부터  reconstruction error를  계산하고, 통계적인 제어 방식을 도입하여 이상을 탐지한다. 관련된 이벤트를 

## 1. Introduction

DBMS는 빅데이터 활용에서 더욱 중요한 부분이 되었다. 제어해야하는 데이터의 양이 증가하여 제어하기 어려워졌기 때문이다. DBMS에서 이상탐지는 다음과 같은 이유로 중요하다.

- DBMS black out과 같은 심각한 결함과 성능 저하를 방지
- DBA가 configuration과 SQL running 포인트를 결정하기 위해

이전에 DBA는 DBMS에 장애가 발생과 함께 이상을 조사하였고 그들의 경험에 의존하여 원인을 파악하였다. 그러나 현대 DBMS를 직접제어 하는것은 인간의 능력을 초과했다. 사이즈와 복잡성이 너무 커졌다.

이상은 도메인과 데이터의 특성에 따라 다르게 정의 할 수 있다. 실무적인 측면에서, 이상을 예측할 수 없거나 설명할 수 없는 변화라고 할 수 있다.  관측될 수 없거나 추론할 수 없는 데이터. 예를 들어 갑작스런 oulier의 증가나 트렌드의 변화는 예측할수 없다는 점에서 이상이라고 할 수 있다. 예측불가능성 접근은 이상치를 찾는것에 적합한 방법이다. 예를 들어 과거에 예측할 수 있는 변화였다면 그러한 변화는 증가하여도 위험이 되지 않는다.

이상탐지는 머신러닝을 적용하기 어렵다. 라벨이 있는 데이터를 만들고 수가 별로 없다. 게다가 이상타지는 DBMS, IT 보안 또는 산업 모니터링에서 매우 중요한 분야이다. 라벨을 만드는 것은 도메인에 있는 전문가에 의존하는 어려운 작업이다. 그러나 전문가를 이용해서 ... 매번 데이터를 만드는것은 비용도 많이 들고 불가능하다. 그러므로 많은 이전 영구에서는 지도학습을 이용하지 못하였다. 특히 시계열데이터는 기존 연구들은 정상 또는 주기적인 데이터로 연구범위를 제한하였다.

빅데이터 기술을 개발하면서, 딥러닝은 이미지, 자연어처리와 같은 다양한 분야에서 뛰어난 성능을 보였다. 딥러닝 모델은 사람이 수작업으로 코딩할 수 없는 숨겨진 표현을 추출하는 것이 가능하다. 그중에서도 딥 오토인코더는 고차원의 데이터를 여러 개의 층을 이용하여 숨겨진 표현을 찾아 낼 수 있다.

본 논문에서는 비정상 데이터에 대해서 오토인코더를 이용하여 reconstruction error를 기반으로 이상탐지하는 것을 제안한다. 제안된 모델은 ...





## 2. Theoretical background

### A. Anomaly detection

이상 탐지는 기존의 관측 패턴을 따르지 않는 예측할 수 없는 특징을 찾는 것을 말한다. 기계학습에서 이것은 학습에 사용할 수 없거나 학습하기에 충분하지 않은 것을 의미한다. 모델 특성에 기초하여 이상탐지는 5가지로 구분된다. 확률 기반, 거리 기반, reconstruction 기반, 도메인 기반, 정보 이론 모델. 특히 nn기반은 이상탐지를 위하여 reconstruction 기반 모델을 활용할 수 있다.

임계치를 결정한게 문제 중 하나이다.

### B. Deep autoencoder

### C. Statitical Process Control

SPC는 프로세스의 결과를 모니터하기 위한 통계적인 모델이다. SPC의 목적은 책임을 돌리수 있는 원인을 찾는것이다. 원인이 존재하는지 아닌지 알기 위해서 control charts는 SPC에서 사용ㅇ된다. 

임계치는 평균 +- 3*표준편차



### D. Non-stationary Time Series

현실에서는 stationary 데이터는 거의 없다.

비정상이라는 것은 시간에 따라 평균과 편차가 변한다는 것을 의미한다. 시계열 데이터는 de-trending, differencing과 같은 기법들을 이용하여 정상데이터로 바꿀 수 있다.

요약하자면 정상 데이터로 바꾸는 것은 필수적인 일이다.



## 3. Proposed model

### A. Problem description

### B. Data

#### 1) DBMS stat metrics

DB 상태에 대한 기본적인 정보를 제공한다. 수백가지가 존재하지만, 6가지 많은 사용한다. DBA와 consultant들 인터뷰를 통해 선정했다.

- CPU used

- Active Session
- Session Logical Reads
- Physical reads
- Execute Counts
- Lock waiting session



#### 2) DBMS event metrics

DBMS event metric은 세션이 쿼리를 요청할때 DB에서 발생하는 대기 정보를 설명한다. 예를 들어 ...

로그랑 유사



### C. Model Scheme

사전에 학습된 모델은 서비스 제공자 관점에서 매우 중요하다. 

사전에 학습된 모델이 없다면 

이상 탐지기가 이상 기간을 찾는경우, 원인 사건을 조사한다. DTW나 Pearson correlation을 이용하여.

### D. Anomaly detector model description

- Batch Temporal Normalizetion Layer



#### E. Batch Temporal Normalization



#### F. Anomaly period detection with SPC

- 



## 4. Experiments

### A. Training results of Deep autoencoder

학습전에 오토인코더의 적절한 hyper-parameter를 찾기 위해 실험을 반복하였다. 레이어 및 뉴런의 수, optimizer, learning rate, regularization parameter, batch size는 경험적인 반복 후에 결정 되었다. Adam optimizer, 0.003, 1500 batch size.

30 window step. 60%, 20%, 20%.

relu.

mean squared error

total time normalized



### B. Anomaly periods detection

DBA가 진단했던 이상을 블라인드로 테스트.

10개의 이상에 대한 테스트



### C. Causal events detection





# Anomaly detection of time series

- abstract

이 논문은 시계열 데이터에서 이상탐지를 어떻게 하는지에 대해서 다루고 있다. 시계열 이상탐지는 헬스 케어, 생태계 시스템 교란, 침입 감지, 항공기 시스템 관리 등에서 중요하게 사용되고 있다.

이상탐지에 대한 광범위한 연구에도 불구하고 ㅏ...

이 논문에서는 우리는 최근기술에 대해서 알아본다. 우리는 이상탐지를 ...



## Introduction

이상은 ... 이상을 찾는 것이 이상탐지. 이상탐지는 조취를 취해야 하는 정보를 준다는 점에서 많은 분야에서 중요하게 생각되고 있다. 예를 들어, 허가되지 않은 곳으로 민감한 정보가 전송되는 것은 해킹이 시도되고 있다는 것을 의미한다. 

많은 도메인에서 시계열 혹은 sequences로 수집되고 있다. 예를 들어 ..... 

이 논문에서는 ... semi-supervised 이상탐지에 집중한다. 



### 1.1 outline

- chapter 2: 
- chapter 3:
- chapter 4:
- chapter 5:



## Anomaly detection for time series

### 2.1 Applications

- Detecting anomolous heart beat pulses using ECG data
- Detection of anomolous flight sequences using sensor data from aircrafts
- Shape anomalies



### 2.2 Problem setting

#### Detecting contextual anomalies in the time series



- setting 1: detecing contextual anomalies in the time series
- setting 2: detecting anomalous subsequence within a given time series
- setting 3: detecting anomalous time series w.r.t a time series data base



1. 정상 데이터는 하나의 생성 과정을 통해 발생된다. 
2. 정상 데이



### 2.3 Challenges for time series anomaly detection

- 특정 이벤트가 시계열 데이터에서 수상할 때, 서브 시퀀스가 이상할때, 전체가 다 이상할때
- 서브 시퀀스의 정확한 길이를 알 수 없다.
- 학습과 시험 할떄의 시계열 데이터 길이가 다르다.
- 유사도나 거리 기반 측정의 경우 데이터 마다 최적의 방법이 무엇인기 알기 어렵다.
- 노이즈에 영향을 받기 쉽다.
- 실생활에서 시계열 데이터는 계속 길이가 증가하므로 계산의 복잡성이 같이 증가한다.
- 스케일 문제



### 2.4 Types of time series data

조사에서 많은 기법들은 정상 데이터에 대한 특징을 학습하고 이상 점수를 계산하는 방식이다. 그러므로 이상 시계열 뿐만아니라 정상에 대한 특성도 모델의 성능에 영향을 미친다. 

priodicity와 synchronous 특징에 대해서. 네 개로



### 2.5 Overview of existing techniques

이상탐지 기법들은 이상탐지를 찾는 과정과 데이터를 변환하는 과정에 따라 분류된다. Procedural dimension, Transformation dimension. 

processdural 관전에서 5가지 기법이 있다. 이러한 기법들은 이상치를 찾는 과정에서 방법이 다르다. 윈도우 기반과 유사도 기반의 방법들은 시험 시계열과 학습 시계열을 비교하는 방법으로 동작하여 레이지 러닝 모델을 만든다. HMM과 regression은 파라메트릭 모델을 만든다. segmentation은 자동으로 만든다.



### 2.6 Transfomation of data

#### 2.6.1 Aggregation



#### 2.6.2 Discretization



#### 2.6.3 Signal processing





### 2.7 Detection Techniques

이전 섹션까지 논의했던 것은 시계열을 어떻게 볼 것인가와 적용하는 기술을 위해 어떻게 처리 할 것인가에 대한 것이었따. 이번 섹션에서는 다양한 이상탐지 기법들을 다룰 것이다. 

1. 이상탐지 기법을 이용하여 각 관측값이나 주어진 테스트 시계열 데이터의 서브 시퀀스에 대한 이상점수를 계산
2. 이상 점수를 aggregate, 1) 이상점수를 평균, 2) 이상 정수 상위 k개를 평균, 3) 이상점수의 로그를 평균, 4) 임계치를 넘는 경우를 카운트



#### 2.7.1 Window based

- strength and weakness

  윈도우 기반의 기술은 윈도우 사이즈를 신중하게 결정해야한다는 단점이 있다. 윈도우 사이즈의 최적화는 이상스런 부분의 길이에 의존해야 한다. 예를 들어 이상한 부분이 시계열 데이터의 주기와 같은 길이를 갖는다. 그러므로 m이 cycle 길이보다 작게 선택된다면 성능이 떨어질 것이고, 반면에 m이 사이클 길이보다 크다면 성능이 좋을 것이다. 다른 단점은 계산에 소모되는 자원이 크게 발생한다. 복잡도는 O((nl)^2), l은 시계열 데이터의 길이 n은 시계열 데이터의 갯수. 대부분의 윈도우 기반 방법들은 2번 문제를 해결하기 위해 사용된다. 

윈도우 기반의 방법들은 



#### 2.7.2 Proximity based

거리 기반의 방법은 test와 training 시계열을 짝으로 사용한다. 정상과 이상한 것 사이에는 차이가 있을 것으로 가정하여 유사도를 측정한다. 

1. k-NN: 
2. Clustering

유사도는 여러가지 방법을 사용할 수 있다. correlation, Euclidean, Cosine, DTW, etc 등으로 유사도/거리를 측정할 수 있다.

유클리디언 거리는 이해하기 쉽고, 빠르게 계산 할 수 있지만, 시계열 데이터의 길이가 다를 경우에는 사용이 불가하다. 또한, 비선형적일 경우 다루기 어렵다. 

DTW는 비선형적인 정렬로 되어있거나 길이가 다른 경우에도 적용이 가능하다. DTW는 정렬해준다. DTW의 단점은 과도하게 매칭하여 알고리즘이 computationally expensive 해지고, 실제거리와의 왜곡을 발생시킨다.

다른 문제는 다른 시간의 데이터는 다른 조건에서 발생되며, 그러므로 동시에 일어나지 않는다. 그러므로 유클리디언과 DTW는 정렬을 맞출 수가 없다. 예를들어 

- 장단점

유사도 기반의 단점은 전체가 이상이 있는지 아닌지를 결정할 수 있으나 정확한 위치를 알 수는 없다. 로컬라이즈하기 위해서는 시계열 데이터에 대한 사후처리가 필요하다. 또한, 위치가 잘못 정렬되거나 비선형적인 ... 이 있는 경우 사용이 제한된다. 그러므로 이러한 기법의 성능은 유사도 측정 방식에 의존한다. 다른 종류의 이상을 감지하는 것은 실패할 확률이 높다.  



#### 2.7.3 Prediction based

1. Time series based
2. General regression (non-time series based)



- 장단점

예측 기반의 기술들의 이슈는 아래와 같다. 윈도우 기반의 문제와 유사하며, 길이를 정하는 것이 이상을 정확하게 가르키는 것에 중요하다. 히스토리 길이가 사이클 길이보다 작으면 성능이 떨어진다. 또한, 고차원 데이터는 sparse 하기 때문에 차원의 저주에 빠진다.

데이터는 통계적인 절차에서 발생되는 것을 가정하기 때문에 가정이 맞다면 성능이 좋다. 

모든 예측 기반의 기법들은 고정된 길이의 history를 사용한다. 같은 시계열에 대해서는 가끔은 작은 게 좋고, 어떤 때는 큰게 좋고. 그러므로 

예측 기반의 기벌들은 이상점수를 계산한다. 



#### 2.7.4 Hidden Markov Models based

- 장단점

HMM 기반의 방법들은 hidden process가 존재해야한다는 가정을 만족해야한다. 가정이 성립하지 않을 경우 이상을 찾을 수 없다.

HMM 기반의 방법들은 시계열 데이터에 대한 markov 모델을 만든다. 그러므로 이것들은 모든 종류의 ....



#### 2.7.5 Segmentaion based

- 장단점

segmentation 기반의 기술들은 균일한 segment의 그룹에서 학습 데이터가 나온 것을 가정한다. 이 경우 

FSA(Finite State Automata)

연산량이 많음.



### 2.8 Discord Detection

discord를 찾기 위한 일반적인 방법은 아래와 같다.

1. t window로 $S_q$를 나눈다. 
2. 각 슬라이드 별로 이상점수를 계산한다. 도우
3. 윈



윈도우 기반의 



## Subspace based transformation for univariate timeseries

### 3.1 Motivation

### 3.2 Detecting anomalies in Multivariate Time series

#### 3.2.1. Subspace Monitoring for Multivariate Time Series

#### 3.2.2 Converting a Multivariate Time Series to Univariate Time Series

### 3.3 Transformation

#### 3.3.1 Methodology

## 4. Experiments and Discussion

### 4.1 Anomaly Detection Techniques

### 4.2 Data Sets Used

- Motor Current Data Set
- Power Usage Data
- NASA Valve Data
- Shape Data
- ECG Data
- EVI Data
- Disk Defect Dataset

### 4.3 Comparison of Anomaly Detection Techniques

### 4.4 Comparison of Original and Transformed Time Series

### 4.5 Observations

### 4.6 Conclusions and Future Work

## 5. Conclusions and Future Work





# Robust Anomaly Detection for Multivariate Time Series through Stochastic Recurrent Neural Network

- Abstract



## 1. Introduction

OmniAnomaly, 

Stochastic: 확률적인.



## 2. Related work

다변량 시계열 데이터 이상탐지는 논의가 많은 주제이다.

지도 학습[17, 20], 라벨 있는 경우 [13]

결정론적 모델[4, 6, 11]

확률론적 모델[16, 27]



## 3. Preliminaries

### 3.1 Problem statement

시계열 데이터는 .

### 3.2 Overall structure



### 3.3 Basics of GRU, VAE and Planar NF



## 4. Design of omnianomaly

### 4.1 Network architecture

### 4.2 Offline model training

### 4.3 Online detection

### 4.4 Automatic threshold selection

Extreme Value Theoryw



### 4.5 Anomaly interpretation



## 5. Evaluation

### 5.1 Datasets and performance metrics

### 5.2 Results and analysis





## 6. Discussion

### 6.1 Visualization on z-space representations

### 6.2 Lessons learned



## 7. Conclusion

## 8. Acknowledgment

