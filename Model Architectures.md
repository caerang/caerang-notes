# Model Architectures

* 단어의 연속적인 표현을 위한 다양한 방법 제안
  * LSA
  * LDA
* 새로운 NN 모델 제시
* 서로 다른 모델간 성능 비교를 위해 시간 복잡도 정의
* 정확도를 최대로 올리면서 시간 복잡도는 낮추는 시도
* 모델 훈련의 복잡도는 다음 식에 비례

$$
O = E\times T \times Q \\

\text{E : training epoch 수}\\
\text{T : training 집합에 있는 단어 수}\\
\text{Q : is defined further for each model architecture}\\
$$

* 모든 모델은 SGD와 BP로 훈련 됨

## Feedforward Neural Net  Language Model (NNLM)

## Recurrent Neural Net Language Model (RNNLM)

## Parallel Training of Neural Networks

# New Log-linear Models

* 새로운 모델 두 가지 제시
* 복잡도의 원인은 비선형 히든 레이어임을 발견
* 신경망처럼 정교하게 데이터를 표현할 수 없을지 모르지만 훨씬 많은 데이터를 효과적으로 훈련할 수 있는  간단한 모델을 실험

## Continuous Bag-of-Words Model



Linear Regularity

