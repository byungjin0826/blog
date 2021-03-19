# UGR`16: A new dataset for the evaluation of cyclostationarity-based network IDSs

- Abastract

침입 감지 시스템이 적용된 기술과 알고리즘을 평가하는 것은 잘 설계된 기존 사례에 의존되었다. 최근 몇년 간 이러한 데이터셋을 만들기 위한 노력들이 계속되었다. 그러나 발전은 없었다. 본 논문에서는 기존의 데이터셋에 대한 리뷰를 하고, 그것들의 단점들을 강조할 것이다. 그리고나서 우리는 새로운 데이터셋에 대해서 소개할 것이다. ...



## 1. Introduction





## 2. Review of exsting datasets

우리는 ...

IDS(intrusion detection system)





### 2.1. Exsiting datasets

IDS 기술이 생겨난 이래로 평가를 위한 좋은 데이터를 만들기위한 많은 노력들이 있었다. 첫번째로는 reference datasets



#### 2.1.1. Reference datasets

##### 2.1.1.1. DARPA datasets

4GB

압축된 binary tcpdump data

7주간

synthetic network traffinc

5M records

2M test data

4victim system

https://www.ll.mit.edu/r-d/datasets



##### 2.1.1.2. KDDCup`99 dataset

4,9M , 41 features.

labeled data

정상과 이상뿐아니라 User to Robot, Remote to Local Probing Attack 등 구분도.

24개의 공격 유형, 



##### 2.1.1.3. Improvements to DARPA datasets





#### 2.1.2. More recent datasets

##### 2.1.2.1. Sperotto





##### 2.1.2.2. MAWI working lab dataset

##### 2.1.2.3. UNB ISCX 2012

##### 2.1.2.4. CTU-13

##### 2.1.2.5. ADFA-LD12

##### 2.1.2.6. UNSW-NB15

##### 2.1.2.7. Application specific datasets

### 2.2. Requirements for IDS evaluation datasets

IDS를 평가하기 위한 이상적인 데이터 셋이 가져야할 특징들을 분석.

1. Features: 데이터셋은 네트워크나 호스트의 특징을 포함해야 한다. 네트워크 특징은 일반적으로 
2. Real background traffic: 실제 traffic을 포함해야한다. 모조의 데이터는 정상 모델과 특징이 정확하지 않다.
3. Updated attack traffic: 
4. Labeling: 
5. Duration: 충분히 긴 기간을 필요로. 주간과 야간, 주말 주중 구별하기 위해
6. Documentation: 
7. Format: cap, csv, flow(long duration)



### 2.3. Comparison of exsiting datasets





## 3. Cyclostationarity in network IDSs

## 4. Dataset generation methodology

### 4.1. Network infrastructure

### 4.2. Attack traffic generation

#### 4.2.1. Implementation of attacks

#### 4.2.2. Attacks executtion scheduling

### 4.3. Dataset captures

### 4.4. Dataset preprocessing and availability

## 5. Dataset analysis and labeling

### 5.1. Dataset figures

### 5.2. Labeling

#### 5.2.1. Signature-based labeling

#### 5.2.2. Anomaly-based labeling

## 6. Conclusion

