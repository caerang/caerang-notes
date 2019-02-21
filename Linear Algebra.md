# Linear Algebra

## Matrix Operations and Manipulations

m행 n열 행렬 A 는 식 (1)과 같이 표현 한다
$$
A_{m \times n} \in \mathbb{R}^{m \times n}
$$

##### 행렬의 덧셈

두 행렬 A, B 의 덧셈은 각 행렬의 원소끼리의 덧셈이다.

만약 행렬 C가 두 행렬 A, B의 덧셈의 결과라면
$$
c_{ij}=a_{ij} + b_{ij} \qquad \forall i \in \{1, 2, ..., m\}, \forall j \in \{1, 2, ..., n\} \qquad where\ a_{ij} \in A, b_{ij} \in B, c_{ij} \in C
$$

##### 행렬의 뺄셈

두 행렬 A, B의 뺄셈은 각 행렬의 원소끼리의 뺄셈이다.

만약 행렬 C가 두 행렬 A, B의 뺄셈의 결과라면
$$
c_{ij} = a_{ij} - b_{ij} \qquad \forall i \in \{1,2, ..., m \}, \forall j \in \{1, 2, ..., n\} \qquad where\ a_{ij} \in A, b_{ij} \in B, c_{ij} \in C
$$

##### 두 행렬의 곱셈 (Product of Two Matrices)

두 행렬 $A \in \mathbb{R}^{m \times n}$와 $B\in \mathbb{R}^{p \times q}$에 대해 곱하기가 성립하려면 n과 p가 같아야 한다.

만약 행렬 C가 두 행렬 A, B의 곱셈의 결과라면
$$
c_{ij} = \sum_{k=1}^{n}a_{ik}b_{kj} \qquad \forall i \in \{1,2,...,m\}, \forall j \in \{1,2,...,q\}
$$
[행렬의 곱셈 예제 추가]

##### 전치 행렬

행렬 $A \in \mathbb{R}^{m \times n}$ 의 전치 행렬은 $A^T \in \mathbb{R}^{n \times m}$ 으로 표기하고 행 백터를 열벡터로 변환한다.
$$
\acute{a}_{ji}=a_{ij} \qquad \forall i \in \{1,2,...,m\}, \forall j \in \{1,2,...n\} \quad where\ \acute{a}_{ji} \in A^T and\ a_{ij} \in A
$$
[행렬의 치환 예제 추가]

##### 벡터의 내적

n 차원 백터를 행렬로 표현하면 $\mathcal{V} \in \mathbb{R}^{n \times 1} $이다. 두 벡터를 $\mathcal{V}_1, \mathcal{V}_2$가 다음과 같다면
$$
\mathcal{V}_1 = 
\begin{bmatrix}
\mathcal{V}_{11} \\
\mathcal{V}_{12} \\
\vdots \\
\mathcal{V}_{1n}
\end{bmatrix},

\mathcal{V}_2 = 
\begin{bmatrix}
\mathcal{V}_{21} \\
\mathcal{V}_{22} \\
\vdots \\
\mathcal{V}_{2n}
\end{bmatrix}
$$
두 벡터의 내적은 대응하는 원소의 곱셈의 합이다.
$$
\mathcal{V}_1 \cdot \mathcal{V}_2 = \mathcal{V}_1^T \mathcal{V}_2 = \mathcal{V}_2^T \mathcal{V}_1 = \mathcal{V}_{11}\mathcal{V}_{21} + \mathcal{V}_{12}\mathcal{V}_{22} + 
\cdots + \mathcal{V}_{1n}\mathcal{V}_{2n} = \sum_{k=1}^n \mathcal{V}_{1k}\mathcal{V}_{2k}
$$

##### 행렬과 벡터의 곱

행렬과 백터의 곱셈 결과로 새로운 벡터가 생성된다.

행렬 $A \in \mathbb{R}^{m \times n}$ 와 벡터 $x \in \mathbb{R}^{n \times 1}$의 곱셈은 새로운 벡터 $b \in \mathbb{R}^{m \times 1}$를 생성한다.
$$
A = 
\begin{bmatrix}
c_1^{(1)}c_1^{(2)}\cdots c_1^{(n)} \\
c_2^{(1)}c_2^{(2)}\cdots c_2^{(n)} \\
\vdots
c_m^{(1)}c_m^{(2)}\cdots c_m^{(n)} \\
\end{bmatrix}, 
\ x = 
\begin{bmatrix}
x_1 \\
x_2 \\
\vdots \\
x_n 
\end{bmatrix}
$$
행렬 A는 n 개의 컬럼 벡터($c^{(i)} \in \mathbb{R}^{m \times 1} \qquad \forall i \in \{1,2,3,...,n\}$)로 이루어져 있다.
$$
A = [c^{(1)}c^{(2)}c^{(3)}\cdots c^{(n)}] \\
b = Ax = [c^{(1)}c^{(2)}c^{(3)}\cdots c^{(n)}]
\begin{bmatrix}
x_1 \\
x_2 \\
\vdots \\
x_n
\end{bmatrix}
= x_1c^{(1)} + x_2c^{(2)} + \cdots x_nc^{(n)}
$$
컬럼벡터와 행렬의 선형 조합이고 벡터 $x​$ 의 요소는 선형 계수이다.

행렬의 곱셈으로 생성된 새로운 백터는 행렬 A 의 컬럼 백터와 동일한 차원을 갖는다. 즉 우리가 얼마나 많은 컬럼 백터를 조합하는지와 상관 없이 컬럼 벡터에 의해 확장된(spanned) 공간을 떠날 수 없다.



##### 벡터의 선형 독립

벡터가 다른 벡터의 선형 조합으로 표현 가능하다면 그 벡터는 선형 종속이라고 이야기 한다.

예를 들어 $\mathcal{V}_1=5\mathcal{V}_2 + 7\mathcal{V}_3$ 이라면 $\mathcal{V}_1, \mathcal{V}_2, \mathcal{V}_3$ 은 선형 독립이 아니다. 왜냐하면 $\mathcal{V}_1$이 $\mathcal{V}_2$와 $\mathcal{V}_3$의 덧셈으로 표현 가능하기 때문이다.

일반적으로 $n$ 개의 벡터로 이루어진 집합($\mathcal{V}_1,\mathcal{V}_2,\mathcal{V}_3,\cdots , \mathcal{V}_n \in \mathbb{R}^{m \times 1}$)은 $a_1\mathcal{V}_1 + a_2\mathcal{V}_2 + a_3\mathcal{V}_3 + \cdots + a_n\mathcal{V}_n=0 이고 a_i=0 \quad \forall i \in \{1,2,\cdots n\}$를 만족하는 경우만 선형 독립이라고 말한다.

[ 내용 추가 정리 필요, 선형 독립과 확장의 관계]



##### 행렬 계수

행렬의 계수는 선형 독립인 컬럼 벡터 또는 로우 벡터의 개수이다. 서로 독립인 컬럼 벡터의 수는 서로 독립인 로우 벡터의 수와 항상 같다.

##### 정리해야 할 내용

* 선형 조합의 정의와 의미