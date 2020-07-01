딥러닝 네트워크에서 과적합(Overfitting) 문제를 해결하는 방법

* 더 많은 데이터를 사용
* Cross Validation
* Regularization

더 이상 학습 데이터를 추가할 수 없거나 학습 데이터를 늘려도 과적합 문제가 해결되지 않을 때, Regularization 사용

Regularization에서는 Loss 함수를 다음과 같이 변형해서 사용
$$
\begin{equation} \label{eq:loss}
cost(W, b) = \frac{1}{m}\sum_i^mL(\hat y^i,y^i) + \lambda\frac{1}{2}\lVert w \rVert ^2
\end{equation}
$$
위 식에서 Weight를 정규화하기 위해 Weight의 L2 Norm을 새로운 항으로 추가

## Norm

* Norm은 벡터의 크기 또는 길이를 측정하는 방법(함수)
* Norm이 측정한 벡터의 크기는 원점에서 벡터 좌표까지의 거리 또는 Magnitude

$$
L_p=\left(\sum_i^n|x_i|^p\right)^\frac{1}{p}
$$

* $ p $ 는 Norm의 차수
* p가 1이면 L1 Norm
* p가 2이면 L2 Norm

[딥러닝을 위한 Norm, 노름](http://taewan.kim/post/norm/)