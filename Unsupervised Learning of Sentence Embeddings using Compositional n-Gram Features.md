# Introduction

# Model

$$
\min_{U,V} \sum_{S \in C}f_S(UV_{\iota S})
$$

* $ U \in \R^{k \times h} ​$ , $ V \in \R^{h \times |V|}​$, V 는 단어 사전, U의 컬럼은 target word vector, V 컬럼은 learnt source word vector
* S 는 임의의 크기를 갖음(당연, 문장의 길이는 다양하니까...)
* indicator vector $\iota S \in \{0, 1\} ^{|\mathcal{V}|}$ is binary vector encoding S (bag of words encoding)
* C-BOW나 GloVe에서와 같이 고정 크기의 context windows사용해서 단어 임베딩
* 논문에서는 $ k = |\mathcal{V}| $ 이고 각 비용 함수(cost function)는 $ f_S : \R^k \mapsto \R $ 이건 기존 단어 임베딩인 경우이고
* 문장 임베딩에서 S는 전체 문장 또는 문서(가변 길이)
* 이런 속성은 FastText 분류기에도 동일한 속성을 공유

## Proposed Unsupervised Model

* 단어 사전 $ w $의 각 단어에 대해 source (or context) 임베딩 $ v_w $과 대상 임베딩 $ u_w $ 를 학습

* 임베딩 차원은 $ h, k = |\mathcal{V}| $

* 문장 임베딩은 문장을 구성하는 단어 임베딩의 평균값으로 정의
  $$
  v_S := \frac{1}{|R(S)|} V_{\iota R(S)} = \frac{1}{|R(S)|} \sum_{w \in R(S)}v_w
  $$
     * $ R(S) $ 는 문장에서 나타내는 n-grams(uni-gram 포함) 리스트

   * 문장에 없는 단어도 예측하려면 negative sampling 을 반영해서 softmax 를 모델링함

   * negative sampling 은 학습 효율성도 개선하는 것으로 알려져 있음

   * binary logistic loss function을 negative sampling 과 결함하면 목적함수는 다음과 같음
     $$
     \min_{U,V} \sum_{S \in C} \sum_{w_t \in S} \left(l(u^T_{w_t}v_{S_{w_t}}) + \sum_{w^{'} \in N_{w_t}} l(-u^{T}_{w^{'}}v_{S_{w_t}}) \right)
     $$
     
     * $ S $ 문장, $ N_{w_t} $ 는 $ w_t \in S $ 에 대해 nagative sampling 한 단어 모둠

* 대상 unigram은 서브샘플링을 통해 선택

* 각 단어는 $ 1 - q_p(w) $ 확률로 제외 됨.

* $ q_p(w) := \min \{ 1, \sqrt{t/f_w}+t/f_w \}$ , $ t $는 서브샘플링 하이퍼파라메터

* 서브 샘플링은 너무 자주 나오는 단어가 학습에 너무 많은 영향을 미치는 것을 방지

* negative sampling 과 positive subsampling을 적용한 목적 함수는 다음과 같음
  $$
  \min_{U,V} \sum_{S \in C} \sum_{w_t \in S} \left(q_{p}(w_t)l(u^T_{w_t}v_{S_{w_t}}) + |N_{w_{t}}|\sum_{w^{'} \in N_{w_t}} q_n(w^{'})l(-u^{T}_{w^{'}}v_{S_{w_t}}) \right)
  $$

## Computational Efficiency

* 학습과 추론에 낮은 계산 비용이 드는 것이 장점
* 주어진 문장 S와 학습된 모델에 대해 문장 표현 $ v_S $의 계산에는 $ |S| \cdot h $ 의 부동소숫점 연산량

* 위 수식에 대해 학습하는 경우도 동일한 연산량만 필요
* 모델이 단순해서 훈련과정에 병렬 처리가 가능함
* 효율적인 고차원 n-gram 저장을 위해 표준 해시 트릭 사용(FastText와 동일한 해시 함수 사용)

## Comparison to C-BOW

## Model Training

# Related Work

## Unsupervised Models Independent of Sentence Ordering

