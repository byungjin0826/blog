---
title: 이상탐지분석
tags: anomaly detection, abnormal
---

## 이상 탐지란?

이상 탐지는 outlier detection, novelty detection, anomaly detection, noise detection, deviation detection or execption minig 등 다양한 용어로 불린다. 

- outlier: a person, thing, or fact that is very different from other people, things, or facts, so that it cannot be used to draw general conclusions; a place that is far from the main part of something;
- novelty: the quality of being  new and unusual; something that has not been experienced before and so is interesting;
- anomaly: a person or thing that is what is unusual, or not in agreement with something else and therefore not satisfactory
- noise: any bad change in a signal, especially in a signal produced by an electronic device; unexplained or unexpected information in a sample that is not useful and that can be ignored
- deviation: the action of doing something that is different from the usual or common way of behaving; a difference from what is unusual or expected
- exception: someone or somtehing that is not in cluded in a rule, group, or list or that does not behave in the expected way

상기 기술한 바와 같이 outlier, novelty, anomaly, noise, deviation, exception은 비슷하면서도 차이가 있다. outlier와 관련된 정의는 사용자와 분야에 따라 다양하며, 보편적으로 쓰이는 정의는 없는 듯 하다. 

~~~
An outlying observation, or outlier, is one that appears to deviate markedly from other members of the sample in which it occurs.
~~~

~~~
An observation (or subset of observations) which appears to be inconsistent with the remainder of that set of data.
~~~



이상 탐지는 안전이 중요한 분야에서 특히 중요한 업무가 된다. outlier는 정상적이지 않은 운영 환경을 의미하며, 항공기 엔진의 결함, 배수로 막힘과 같은 문제들을 야기한다. outlier는 

- time-series monitoring
- detecting novelty in text
- activity monitoring
- network performance



outlier는 humman error, 측정 error,  분포에서 자연적인 벗어남, 허위 행위, 시스템의 특성 변화 또는 결함 등에 의해 발생된다. 어떻게 outlier detection system이 outlier를 다룰지는 적용 분야에 따라 다르다. 

## 이상탐지 종류

### Type 1

데이터에 사전 지식이 없이 outlier를 결정하게 되는 경우. 이경우 비지도 학습과 유사한 방식의 접근이 필수적이다. type1은 에러나 결함은 "정상적인" 데이터와 분리되어 있으며, outliers로 발견될 수 있다는 것을 가정한다(fig 3).

![image-20210304151920010](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210304151920010.png)



main cluster와 하위 그룹으로 나눌 수 있는 경우(fig 4). 이 경우에는 배치 프로세싱과 유사한 접근 방식을 적용할 수 있다. 처리하기 전에 모든 데이터에 접근이 가능해야하며, 데이터가 정적이어야 한다. 

![image-20210304151930462](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210304151930462.png)



### Type 2

normality와 abnormality가 모두 있는 경우. 이 경우에 지도 학습과 유사한 방식으로 할 수 있으며 사전에 라벨이 입력되어있는 데이터(pre-labelled)가 필요하다. 



### Type 3

모델이 정상만 있거나 이상에 대한 케이스가 매우 적은 경우, semi-supervised recognition or detection과 유사한 방법. 정상 범위를 정하기 위해서 사용된다. 이 경우 정상에 대한 데이터가 많아야 일반화를 할 수 있다. 



![image-20210304151941624](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210304151941624.png)



![image-20210304151952129](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210304151952129.png)

## 통계적 모델 (Statistical models)

### Proximity-based techniques

type1과 type2에 적합한 방법이다. 레코드 수에 따라 컴퓨터 연산량이 지수적으로 증가한다. 

### Parametric methods



### Non-parametric method



### Semi-parametric method



## Neural Networks

### Supervised neural methods

### Unsupervised neural methods

## Machine learning

## Hybrid systems







## anomaly와 outlier의 차이

outlier는 

Outlier: a value that you predictably find in your data that indicates your model does not work properly

Anomaly: a value that against all odds you find in your data that indicates your model does work properly

- 



## 이상탐지의 어려움



- 
- 
- 
- Outlier Detection, DOI 10.1007/978-1-4899-7993-3_80719-1

~~~
outlier detection은 데이터베이스에서 unusual한 데이터(다른 말로 대다수를 차지하는 데이터와는 다르고 그러므로 오염(contamination), 오류이거나 허위를 야기하는 의심스러운)를 식별하는 것을 목표로 하고 있다. 통계적인 모델에서는 "being unusual"을 평가하기 위해서 일반적으로 데이터의 파라메트릭 모델을 기본으로 하고 있다. 모델의 분포와 일치 하지 않는 데이터를 식별한다. 데이터베이스에서는 통계적 직관을 어림하지만 더 효과적이다. density estimates와 reference set과의 비교를 통한다.
~~~

- outlier

- anomaly

- abnormal

- unusual

- specious

- rare



- 

Outlier detection aims at identifying those objects in a database that are unusual, i.e., different than the majority of the data and therefore suspicious resulting from a contamination, error, or fraud. In a statistical modeling, the assessment of “being unusual” is typically based on a parametric model of the data, identifying those objects that do not fit well to the modeled distribution as outliers. In the database context, the statistical intuition of “being unusual” is typically modeled in an approximate but more efficient, nonparametric way by (local) density estimates and comparison to some reference set.