# Neural Machine Translation of Rare Words with Subword Units

## Abstract

## Introduction

* 기계 번역에서 인상깊은 성과가 있었다

* 드문 단어(rare words) 번역은 해결해야 할 문제다.

* 통상 신경망 모델 사전은 3만 에서 5만 단어로 제한되지만 번역은 단어 조합을 갖고 있는 언어 모델

  > * 번역 문제는 open-vocabulary 문제 (사전에 없는 단어, 알수 없는 단어가 출현할 수 있음)
  >
  > * 자연어에서 말하는 vocabulary는 말뭉치를 이야기 하는 건가?

  * (독일어를 예로 듬)에서 해결해야 할 문제

  > 고정된 크기로 단어를 인코딩하는기 기존 방식인 듯. 하지만 언어는 언어 고유한 특성에 따라 고정된 크기를 넘어가는 경우도 생김

* 단어 기반의 NMT 모델에서 단어 사전에 없는 단어 번역은 back-off를 통해 사전 색인(dictionary look-up)에 표시한다.

* 하지만 이런 방법은 실용적으로 사용할 수 있다고 여기지 않는다.

* 두 언어 사이에 형태적인 합성 정도에 차이로 인해 입력/출력 사이에 1대1 대응되지 않는 경우가 있다. (복합 명사 같은 경우가 그 예임)

* 단어 기반 모델은 알지 못하는 단어를 생성하거나 번역할 수 없다.

* 형태학적 변화와 음역이 종종 필요하다.

* subword 단위로 동작하는 모델을 연구했다. 

* 드문 단어(rare words)에 대해 back-off 모델을 사용하지 않고 열린 사전(open-vocabulary) 번역을 모델하는 것이 연구의 목표

  > n-gram 으로 문장에 있는 단어의 확률을 계산할 수 없을 때 n-1 gram을 사용해서 단어의 확률을 계산하는 방법이 back-off 모델

* 훈련 과정에서 보지 못했던 단어를 생성하고 large-vocabulary 모델과 back-off 사전 방법 보다 정확도가 더 높다.

* subword 표현으로 복합 단어와 음역 단어를 학습할 수 있다.

* byte pair encoding 을 단어 분할에 적용함



## Neural Machine Translation

* Bahdanau et al. 아키텍처 적용
* NMT는 RNN을 사용해서 encoder-decoder 네트워크로 구현된다.
* 인코더는 gated recurrent units을 갖고 있는 bidirectional neural network이다.
* 디코더는 대상 단어 수열을 예측하는 recurrent neural network이다.



# Subword Translation

## Related Work

* 통계적 기계 번역(Statistical Machine Translation, SMT) 에서 알지 못하는 단어 번역은 연구가 많이 이루어지는 주제
* 많은 부분이 명칭과 관련되어 있고 영어 알파벳을 사용하는 나라에서는 알파벳 그대로 사용하고 그렇지 않다면 음역을 사용한다
* 문자 기반 번역은 절 기반 모델과 함께 연구 됨(밀접한 언어 사이에 성공적인 결과를 보임)
* 형태학적으로 복잡한 단어 분할은 SMT에 광범위하게 사용 되었고 morpheme 분할과 관련한 다양한 알고리즘이 제안됨
* 절 기반 SMT에 사용된 알고리즘은 분할 결정에 보수적인 성향을 보임
* 의도하는 것은 보다 적극적으로 분할이 가능하며 단출한 네트워크 모델과 back-off dictionaries 에 의지하지 않고 open-vocabulary translation 문제에 적용할 수 모델을 지향함
* 최적의 subword 단위 선택은 작업에 따라 다르다.

## Byte Pair Encoding (BPE)

* BPE(Byte Pair Encoding) 은 문자열에서 출현 빈도가 높은 바이트쌍을 사용하지 않은 바이트 하나로 대체하는 압축 방법
* 단어 분할에 BPE 알고리즘 사용
* 출현 빈도가 높은 바이트를 통합하는게 아니라 문자나 문자의 수열을 통합
* symbol vocabulary 를 character vocabulary로 초기화
* 각 단어를 문자 수열로 표현하고 특별히 종료 단어 기호 '.'를 추가 함 
* 번역 후에 원본 토크나이즈를 복원할 때 사용
* 반복적으로 기호 쌍을 수를 세고 가장 출현 빈도가 높은 기호쌍을 새로운 기호로 대체함
* 매 병합 연산은 문자 n-gram 을 나타내는 새로운 기호를 생성함
* 자주 나타나는 문자 n-gram들은 결국 하나의 심볼로 통합 됨
* 최종 심볼 vocabulary 크기는 초기 vocabulary 와 같은 크기임
* 병합 연산 회수는 알고리즘의 하이퍼파라메터임 
* 효율을 위해 교차 단어 경계에 있는 기호 쌍은 고려하지 않음
* 알고리즘은 문장에서 단어의 출현 빈도에 따라 가중치가 부여된 단어로 구성된 사전에서 수행됨
* 다른 압축 알고리즘과의 차이는 제안한 알고리즘이 subword 단위로도 해석 가능하다는 것임
* 이는 네트워크가 새로운 단어(훈련 과정에서 보지 못했던 단어)를 생성하고 번역하는 것을 일반화 할 수 있다는 것임

참고 자료

* [Open Vocabulary Analysis](https://www.youtube.com/watch?v=ZdTeDED9h-w)
* [Machine Translation - 07: Open-vocabulary Translation](http://homepages.inf.ed.ac.uk/rsennric/mt18/7_4up.pdf)
* [What is backoff in NLP?](https://www.quora.com/What-is-backoff-in-NLP)



알아야 할 개념

* open-vocabulary translation
* back-off dictionary

