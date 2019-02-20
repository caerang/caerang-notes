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
c_{ij}=a_{ij} + b_{ij} \qquad \forall i \in \{1, 2, ..., m\}, \forall j \in \{1, 2, ..., n\} \\
\\
a_{ij} \in A, b_{ij} \in B, c_{ij} \in C
$$

##### 행렬의 뺄셈

두 행렬 A, B의 뺄셈은 각 행렬의 원소끼리의 뺄셈이다.

만약 행렬 C가 두 행렬 A, B의 뺄셈의 결과라면
$$
c_{ij} = a_{ij} - b_{ij} \qquad \forall i \in \{1,2, ..., m \}, \forall j \in \{1, 2, ..., n\} \\
a_{ij} \in A, b_{ij} \in B, c_{ij} \in C
$$

##### 두 행렬의 곱셈 (Product of Two Matrices)

두 행렬 $A \in \mathbb{R}^{m \times n}$와 $B\in \mathbb{R}^{p \times q}$에 대해 곱하기가 성립하려면 n과 p가 같아야 한다.

만약 행렬 C가 두 행렬 A, B의 곱셈의 결과라면
$$
c_{ij} = \sum_{k=1}^{n}a_{ik}b_{kj} \qquad \forall i \in \{1,2,...,m\}, \forall j \in \{1,2,...,q\}
$$
[행렬의 곱셈 예제 추가]

##### 전치 행렬

행렬 A \in \mathbb{R}^{m \times n} 의 전치 행렬은 A^T \in \mathbb{R}^{n \times m} 으로 표기하고 행 백터를 열벡터로 변환한다.
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
