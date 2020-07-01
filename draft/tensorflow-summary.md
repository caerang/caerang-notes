https://www.tensorflow.org/guide/low_level_intro



텐서플로우를 이해하기위해 필요한 기본 개념

* computation graph,
* operations
* sessions
* estimators

Tensorflow program (tf.Graph)은 딥러닝 네트워크 그래프를 생성하는 과정인 것 같고

Tensorflow runtime(tf.Session) 은 실행하는 것?

Tensorflow operations는 tf.Session을 사용해서 실행하고

사용할 환경이 된다면 고차원 API를 사용하는 것을 권장

### TensorFlow Core Walkthrough

텐서플로우로 프로그래밍을 한다는 건 두 단계의 과정으로 생각할 수 있음

* computational graph 생성
* computational graph 실행

#### Graph

