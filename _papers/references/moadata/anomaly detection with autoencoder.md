# GEE: A Gradient-based Explainable Variational Autoencoder for Network Anomaly Detection

- Abstarct

이 논문은 NetFlow rocords를 분석하여 이상을 탐지하는 것에 대한 문제를 고찰하기 위한 것이다. 많은 이전 연구에서는 통계적인 방법과 기계학습을 이용하여 지도학습 하였으나, 이러한 방법들은 많은 양의 라벨된 데이터가 필요하다는 한계점과 제로 데이 공격은 탐지가 불가하다. 기존 이상 탐지 해결 방법ㅇ들은 공격들에 대한 구별과 설명할 수 있는 방법들을 제공하지 않는다. 이러한 한계를 해결하기 위해 GEE를 개발 및 설명할 것이다. GEE는 두 가지로 구성된다. VAE와 gradient-based fingerprinting techniques. GEE를 

## 1. Introduction

## 2. Related work

## 3. Unsupervised Deep Learning Models

## 4. GEE

우리의 이상탐지 GEE는 다음과 같은 메인 스텝으로 구성된다. 첫번째, feature extraction.

normal behaviour 러닝

reconstruction errors

gradient information for explanation and fingerprinting



### A. Feature extraction

3-minute sliding window, 

53 agreegated features.

0-1 scaling

z-score normalized



### B. Unsupervised learning of VAE





### C. Anomaly detection

95% 신뢰도와 같이 매우 적은 확률.



### D. Gradient-based Explanation for anomalies





## 5. Dataset and evaluation

평가를 위해 우리는 UGR16 데이터셋을 활용했으며, 익명화 된 NetFlow 추적을 포함한다. ISP는 

UGR trace는 최근 데이터이며 충분히 큰 데이터를 보함하고 있다.



### A. Baseline

Gaussian Based Thresholding (GBT) 방식. 

### B. ROC performance on Anomaly detection

### C. Identifying and using gradient fingerprints



### D. Clustering of anomalies

### E. Processing overhead of VAE

## 6. Conclusion

