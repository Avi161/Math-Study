# Discrete Least Squares Problem
## Theorem 1.1

Suppose $A \in \mathbb{R^{mxn}}$ with $m \geq n$ and $b \in \mathbb{R^{m}}$. A vector $x \in \mathbb{R^{n}}$ minimizes $\|r\|_2$ if and only if r is orthogonal to the range of A; that is,

$$ <b-Ax, Au> \, = \, <A^{T}b - A^{T}Ax, u> \, = \,  0 \quad \forall u \in \mathbb{R^m} \quad (1)$$
Note, $(1)$ is equivalent to $A^{T} b= A^{T}Ax$, which is uniquely solvable if and only if A has a full rank.
This is because $A^{T}A \in \mathbb{R^{nxn}}$ needs to have a full rank in order to be uniquely solvable. This is only possible when A has full rank (i.e. columns of A are linearly dependent). See, [[THM_P_LA_0.1]]


## Proof:


