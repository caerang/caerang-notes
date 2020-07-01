# Deep Feedforward Networks

* Deep feedforward networks, feedforward neural networks, multilayer perceptrons (MLPs) 라고 불리는 네트워크는 딥러닝 모델의 전형적인 예임
* feedforward 의 목적은 함수 $f^{*}$를 근사화 하는 것임
* 예를 들어 분류기에 대해 $y=f^{*}(x)$ 는 입력 $x$ 를 분류 $y$ 에 매핑 하는 함수로 생각할 수 있음
* feedforward 네트워크는 매핑($y=f(x;\theta)$)을 정의하고 최적의 결과를 도출하는 파라메터 $ \theta $ 의 값을 학습함
* 이런 모델은 feedforward 라고 불림
  * 입력으로 부터 평가될 함수를 통과하고, 함수 $f$ 를 정의하기 위해 사용한 중간 계산들을 통과하고 최종적으로 결과로 정보가 흐르기 때문
  * 입력에서 출력으로 한 방향으로 정보가 흐르기 때문
  * 모델의 출력이 모델에 다시 정보를 제공하는 feedback 연결이 없음
  * 만약에 feedforward 네트워크를 피드백 연결을 포함하는 네트워크로 확장한다면 그 네트워크는 recurrent neural networks 라고 함
* 중요한 상용 어플리케이션의 근간이 되는 네트워크 모델임
* feedforward 네트워크는 recurrent 네트워크로 가는 개념적인 디딤돌임 (자연어 처리에서 두각을 나타내고 있는 RNN)
* 모델은 함수의 합성 방법을 설명하는 방향 비순환 그래프(directed acyclic graph)와 연관이 있음
* 예를 들어 $f(x)=f^{(3)}(f^{(2)}(f^{(1)}))$ 과 같이 세 개의 함수가 연결되어 있을 수 있음
* $f^{(1)}$ 은 첫 번째 레이어 $f^{(2)}$ 은 두 번째 레이어 $f^{(3)}$ 은 세 번째 레이어 라고 부름
* 함수 연결의 길이를 모델의 깊이(depth) 라고 함
* feedforward 네트워크의 마지막 레이어를 출력 레이어 라고 함
* 네트워크를 학습하는 동안에 $f(x)$ 를 $f^{*}(x)$ 에 일치하도록 추정함

