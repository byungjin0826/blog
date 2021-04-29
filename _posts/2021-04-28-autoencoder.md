---
title: Autoencoder
tags: autoencoder, anomaly detection, 오토인코더, 이상 탐지
---

## 오토인코더(Autoencoder)

오토인코더는 인공신경망을 활용한 비지도학습의 일종이다. 그림과 같이 오토인코더는 인코더와 디코더가 합쳐진 구조이다. 오토인코더에는 두 가지 주요한 특징이 있다. 첫번째 특징은 입력 데이터와 최대한 비슷하게 출력하도록 학습된다는 것이다. 학습 과정에서 별도의 라벨이나 타겟 변수가 필요없다. 입력 데이터 그 자체를 학습한다. 두번째 특징은 보틀넥 효과를 주기위하여 인코더의 출력차원을 입력데이터 차원보다 작게 한다는 것이다. 이러한 제약으로 인하여 인코더는 입력데이터의 특징을 효과적으로 추출할 수 있도록 학습된다. 인코더의 역할과 출력을 특징 추출(feature extraction), manifold, 잠재 공간(latent space) 등으로 부르기도한다. 이 글에서는 잠재 공간으로 통일해서 사용할 것이다. 디코더의 역할은 축소된 잠재 공간에서 원래의 데이터를 복원하는 것이다. 일반적으로 잠재공간에서 데이터의 손실이 발생하기 때문에 복원(reconstruct)된 데이터는 원본에 비해 흐려지는 현상(blurry)이 발생하기도 한다.

인공신경망 연구 초기에는 노드의 초기값 학습을 위해 사용하였다. 오토인코더 구조로 학습하여 각 레이어를 반복하여 학습시켜 초기값으로 사용하였다. 오토인코더의 활성함수를 선형 함수로 구성하면 잠재 공간이 PCA와 유사하게 차원을 축소할 수 있는 특징이 있다. 가장 간단한 구조의 오토인코더는 아래와 같이 구성할 수 있다. 케라스를 이용하여 코드를 쉽게 구성할 수 있다. 그러나 오토인코더의 다양한 변형들을 만드는 것에 제약이 있으므로 아래와 같이 클래스를 새로 만드는 것을 추천한다. variational autoencoder, adversarial autoencoder 등은 loss와 train step 등이 복잡하게 정의된다. keras.Model을 상속받아 metrics와 train_step 메소드를 오버라이드 하였다. 오버라이드, 데코레이터, 클래스, 프로퍼티, 텐서플로우 tf.function에 대한 이해가 필요하다.

~~~python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.layers import Input, Dense
from tensorflow.keras.models import Model

latent_space_dim = 2

# encoder structure
encoder_inputs = Input((784, ))
encoder_outputs = Dense(latent_space_dim, activation='linear')(encoder_inputs)
encoder = Model(encoder_inputs, encoder_outputs)

# decoder structure
decoder_inputs = Input((latent_space_dim, ))
decoder_outputs = Dense(784)(decoder_inputs)
decoder = Model(decoder_inputs, decoder_outputs)

# autoencoder
class Autoencoder(keras.Model):
    def __init__(self, encoder, decoder):
        super(Autoencoder, self).__init__()
        self.encoder = encoder
        self.decoder = decoder
        self.loss_tracker = tf.keras.metrics.Mean(name='loss')
        
    @property
    def metrics(self):
        return [
            self.loss_tracker
        ]
    
    @tf.function
    def train_step(self, data):
        with tf.GradientTape() as tape:
            z = self.encoder(data)
            recon = self.decoder(z)  # reconstruction for original data
            loss = tf.keras.losses.mean_absolute_error(data, recon)  # loss
            
        gradients = tape.gradient(loss, self.trainable_weights)
        self.optimizer.apply_gradients(zip(gradients, self.trainable_weights))
        self.loss_tracker.update_state(loss)
        
        return {
            'loss': self.loss_tracker.result()
        }
    
autoencoder = Autoencoder(encoder, decoder)
autoencoder.compile(optimizer='adam')
~~~



테스트 데이터는 mnist를 활용하였다.  

~~~python
from tensorflow.keras.datasets.mnist import load_data

(train_x, train_y), (test_x, test_y) = load_data()  # load data
train_x, test_x = train_x.reshape(-1, 784)/255., test_x.reshape(-1, 784)/255.  # reshape and scale data
~~~



학습 실행코드는 아래와 같다. batch_size는 GPU 성능에 따라 설정값을 조절이 필요할 수도 있다. 

~~~python
autoencoder.fit(train_x, batch_size=6000, epochs=1000)
~~~



아래 코드로 loss 값을 그래프로 표현할 수 있으며, 결과는 아래 이미지와 같다.

~~~python
import matplotlib.pyplot as plt


plt.plot(autoencoder.history.history['loss'])
~~~



