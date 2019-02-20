# Abstract

# Introduction

* 기계 번역에서 인상깊은 성과가 있었다
* 드문 단어(rare words) 번역은 해결해야 할 문제다.
* 통상 신경망 모델 사전은 3만 에서 5만 단어로 제한되지만 번역은 단어 조합을 갖고 있는 언어 모델(독일어를 예로 듬)에서 해결해야 할 문제

> 고정된 크기로 단어를 인코딩하는게 기존 방식인 듯. 하지만 언어는 언어의 고유한 특성에 따라 고정된 크기를 넘어가는 경우가 생기기도 하는 듯.

* 단어 기반의 NMT 모델에서 단어 사전에 없는 단어 번역은 사전 색인(dictionary look-up)에 back-off를 통해서 나타낸다
* 실용적인 면에서 문제가 있다. 두 언어 사이게 형태적인 합성 정도에 차이로 인해 입력/출력 사이에 1대1 대응되지 않는 경우가 있다. (복합 명사 같은 경우가 그 예임)
* 단어 기반 모델은 알지 못하는 단어를 생성하거나 번역할 수 없다.
* 형태학적 변화와 음역이 필요한 경우도 있다.
* subword 단위로 동작하는 모델을 연구했다. 
* 드문 단어에 대해 back-off 모델을 사용하지 않고 열린 사전(open-vocabulary) 번역을 모델하는 것이 연구의 목표
* 훈련 과정에서 보지 못했던 단어를 생성하고 large-vocabulary 모델과 back-off 사전 방법 보다 정확도가 더 높다.
* subword 표현으로 복합 단어와 음역 단어를 학습할 수 있다.
* byte pair encoding 을 단어 분할에 적용



# Neural Machine Translation

* Bahdanau et al. 아키텍처 적용
* NMT는 RNN을 사용해서 encoder-decoder 네트워크로 구현된다



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





참고 자료

* [Open Vocabulary Analysis](https://www.youtube.com/watch?v=ZdTeDED9h-w)
* [Machine Translation - 07: Open-vocabulary Translation](http://homepages.inf.ed.ac.uk/rsennric/mt18/7_4up.pdf)



알아야 할 개념

* open-vocabulary translation
* back-off dictionary

