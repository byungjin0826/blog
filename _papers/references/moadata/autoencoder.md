# Autoencoders

- abstarct

오토인코더는 인공신경망의 일종으로 입력 데이터를 압축되고 의미있는 표현(compressed and meaningful representation)으로 부호화하는 인코더와 가능한한 원래의 것과 유사하게 복호화하는 인코더로 구성된다. 이번 챕터에서는 최근에 주로 쓰이는 여러 종류의 오토인코더를 조사하였다. 또한 오토인코더의 여러 적용과 실제 사례를 설명할 것이다.



## 1. Autoencoders

오토인코더는 입력을 재구성(reconstruct)하기 위해 학습된 인공신경망으로 처음 소개되었다. 이것의 주요한 목적은 정보를 제공하는(informative) 표현을 학습하는 것이다. 이것의 문제는 다음과 같은 수식으로 정리된다.

이것이 가장 일반적인 오토인코더의 모습이다. 특별한 경우 A와 B는 선형 연산이며, 선형 오토인코더를 얻을 수 있다. 비선형 연산을 제거할 경우 PCA와 유사한 결과를 얻는다. 그러므로, 오토인코더는 사실 PCA의 일반화된(generalization) 형태이다. 반면에 낮은 차원을 찾는 것 대신에 비선형 manifold를 학습할 수 있다. 

오토인코더는 끝에서 끝까지 학습하거나 레이어 바이 레이어로 점진적으로 학습할 수 있다. 후자의 경우 이것들을 쌓아서(stacked) deeper 오토인코더를 만들 수 있다. 잡음을 제거하는 convolution 오토인코더도 있다.

이번 챕터는 다음과 같이 구성된다. 섹션 2에서는 오토인코더를 정규화(regularization)하기 위한 기술들에 대해 다루며, 이것들은 압축된 표현들이 의미있게 하는 것을 보장한다. 섹션 3에서는 variational autoencoder를 설명하며, 가장 유명한 형태의 오토인코더이다. 섹션 4에서는 가장 일반적은 적용에 대해서 다루고, 섹션 5에서는 최근 기술들을 센션 6은 결론이다.



## 2. Regularized autoencoders

적절한 정규화가 필요하다. 가장 일반적인 것은 representation의 차원을 입력보다 작게 만드는 것이다. 이것은 보틀넥이라고 불린다. 데이터의 압축과 feature extraction 등의 목적으로 사용된다. 보틀넥은 하나의 노드로 압축되지만, 그래도 오버피팅의 위험성이 여전히 있다는 점을 주의해야한다. 인덱스의 크기보다 인코더의 ..이 더크면.

이러한 경우 

가장 중요한 tradeoff는 bias-variance tradeoff이다. 우리는 인풋을 잘 재구성(reconstruct)하기를 바란다. 반면에 의미있는 표현으로 잘 일반화 되길 바란다. 

### 2.1 Sparse Autoencoders

### 2.2 Denoising Autoencoders

### 2.3 Contractive Autoencoders





## 3. Variational Autoencoders

### 3.1 The Reparameterization Trick

### 3.2 Example: The Case of Normal Distribution

### 3.3 Disentagled Autoencoders

## 4. Applications of autoencoders

### 4.1 Autoencoders as a generative model

### 4.2 Use of Autoencoders for classification

### 4.3 Use of Autoencoders for clustering

### 4.4 Use of autoencoders for anomaly detection

이상탐지는 또다른 비지도 학습니다. 이것의 목적은 정상 데이터의 예시만으로 정상에 대한 프로필을 만들고 이것과 일치하지 않는 데이터를 이상으로 분류한다. 이것은 사기 방지나, 시스템 모니터링 등에 적용될 수 있다. 오토인코더를 활용한 task는정상 샘플의 잠재적인 서브스페이스를 학습 해야한다. 이것이 학습 되면 정상에 대해서는 작은 복원에러가 발생하고 이상일 경우 크게 발생된다.

1. Mem- orizing normality to detect anomaly: Memory-augmented deep autoencoder for unsupervised anomaly detection
2. Deep autoencoding gaussian mixture model for unsupervised anomaly detection



### 4.5 Use of autoencoders for recommendation systems

### 4.6 Use of autoencoders for dimensionality reduction

## 5. Advanced autoencoder techniques

### 5.1 Adversarially learned inference

### 5.2 Deep feature consistent variational autoencoder

### 5.3 Conditional image generation with PixelCNN decoders

## 6. Conclusion

