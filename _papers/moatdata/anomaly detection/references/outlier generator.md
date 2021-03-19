# A Synthetic Data Generator for Clustering and Outlier Analysis

- Abstract

우리는 모조의 데이터를 만들기 위해 분포 기반과 transformation 기반의 접근을 설명할 것이며, 이러한 접근들은 클러스터링과 이상탐지를 위한 여러 종류의 다차원 데이터 셋을 만드는것에 효과적이다. 우리는 data generating system을 만들었다.

하나는 균등분포고 다른 하나는 정규 분포. 

## 1. Introduction

## 2. Exsting Work on Synthetic Data Generation

### 2.1 IBM Quest Synthetic Data Generator

### 2.2 Synthetic Data Generation in Other Research Fields

## 3. Mathematical Tools and Techniques

### 3.1 Uniform Distribution

### 3.2 Normal Distribution

### 3.3 Box-muller Transformation

### 3.4 Linear Transformation

## 4. A Comprehensive Approach to Synthetic Data Generation

### 4.1 Generation of Clustering in a Dataset

#### Datasets with Difficulty Level One

#### Datasets with Difficulty Level Two

#### Datasets with Difficulty Level Three

#### Datasets with Difficulty Level Four

#### Datasets with Difficulty Level Five

### 4.2 Generation of Outliers/Noise in a Dataset

이전 챕터에서 이상과 잡음은 실제 데이터에서는 피할 수 없다는 것을 언급했다. 이상과 잡음을 더하는 메커니즘은 모조 데이터를 만드는 시스템에서 중요한 기여를 한다. 명확한 구분은 없지만 아래의 논의와 같이 이상에 대해서 일반화 해보려고 한다.

이상치는 나머지 데이터와 일치 하지 않는다. 많은 기존 이상탐지 방법들은 밀도 기반으로 분석. 이러한 정의는 문제가 있다.

 While intuitive, such definition raises new issues: how do we specify the cutoff density value to guarantee real outliers and meaningful clusters?

![image-20210317105546644](/Users/byungjinshin/Library/Application Support/typora-user-images/image-20210317105546644.png)

이상을 정의하는 것은 주관적이기 때문에 상황에 따라 이상과 정상에 대한 의견이 모호하다. 

데이터 오브젝트는 다른 방법을 사용해도 정상 범위가 동등해야한다. 그러므로, 지역 또는 전역적으로 이상을 생성하기 위해서는 기존에 있는 이상탐지 기법으로도 객관적으로 분류될 수 있는 데이터를 만드는 것에 집중한다.

클러스터 데이터를 발생시키는 것과 유사하다. 정규 분포와 선형 변환을 사용했다. 이상의 분포와 밀도는 이상 레벨이라는 파라미터에 의해서 결정된다. 



#### Outliers Level None

레벨논은 self-explaining이다. 이상을 추가하지 않는다. 그러나 이것이 반드시 생성된 데이터에 이상이 없는 것을 의미하지는 않는다. 



#### Outliers Level Low

randomly distributes



#### Outliers Level High

랜덤하게 이상을 추가하는 것에 더하여, 제어된 모양과 분포를 더한다. 

1. points that are located in a sparse neighborhood;
2. exterior points of the cluster that a normal distribution;
3. points that form certain patterns, such as the lines, each of which can



## 5. Experiments and Evaluation

### 5.1 Generating Very Large Datasets

### 5.2 Testing with Clustering and Outlier Analysis Algotithms

## 6. Conclusion