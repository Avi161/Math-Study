
# 1. Discrete Least Squares Problem

## 1.1 Linear Algebra Fundamentals

 - Why is $(AB)^{T} = B^{T}A^{T}$ ?
	- Recall, if $A \in \mathbb{R^{n \times m}}$ and $B \in \mathbb{R^{m \times p}}$, then, 
		- $(AB)_{ik} = \sum_{j=1}^{n}{A_{ij}B_{jk}}$ where $i \in [1,m]$ and $k \in [1, p]$
		- $AB$ is a $m \times p$ matrix; ($m,n,p \in \mathbb{N}$)
	- Also, by the definition of transpose, $A_{ij}^{T} \leftarrow A_{ji}$
	- LHS: $(AB)^{T}_{ik}= (AB)_{ki} = \sum_{j=1}^{n}{A_{kj}B_{ji}}$
	- RHS: $(B^T A^T)_{ik} = \sum_{j=1}^{n} (B^T)_{ij} (A^T)_{jk} = \sum_{j=1}^{n} B_{ji} A_{kj}$
	- Hence: $(AB)^{T}=B^{T}A^{T}$

- What is range of $A$?
	- Let $A \in \mathbb{R^{n \times m}}$ 
	- $Range(A) = \{Ax \mid x \in \mathbb{R^{m}}\}$
	- Let $(a_{1}, a_{2}, \dots, a_{m})$ be the columns of $A$ and $x = (x_{1},x_{2}, \dots, x_{m})$. By the definition of matrix vector multiplication, $Ax = a_{1}x_{1}+a_{2}x_{2}+\dots+a_{m}x_{m}$.  Since $x$ is arbitrary, $Ax$ is essentially linear combination of columns of $A$. Hence, ***range of $A$ is equivalent to the column space of $A$.*** 

- What is rank and full rank?
	- Terminology for the least-squares setting, where $A \in \mathbb{R}^{n \times m}$ with $n \geq m$ (tall, skinny matrix):
	- $\text{rank}(A)$ = dimension of the column space = max number of linearly independent columns.
	- For a tall matrix, **full rank** means $\text{rank}(A) = m$, i.e. all $m$ columns are linearly independent. This is sometimes called "full column rank."
	- $A$ has full column rank $\iff$ the only solution to $Ax = 0$ is $x = 0$.

- $A^{T}A$ is nonsingular $\iff$ $A$ has a full column rank
	- For any matrix $X \in \mathbb{R^{n \times n}}$, $X$ is nonsingular $\iff$ $det(X) \neq 0$
	- Proof: [[THM_P_LA_0.1]]

## 1.2 Inner Products, Norms, and Orthogonality

- What is an inner product?
    - On $\mathbb{R}^{n}$, the standard inner product (dot product) is:
        - $\langle x, y \rangle = x^{T}y = \sum_{i=1}^{n}{x_{i}y_{i}}$
    - Three viewpoints:
        - Algebraic: multiply components, sum them up.
        - Geometric: $\langle x, y \rangle = \|x\|_{2}\|y\|_{2}\cos\theta$, where $\theta$ is the angle between $x$ and $y$. Measures alignment.
        - Length: $\langle x, x \rangle = \sum_{i=1}^{n}{x_{i}^{2}} = \|x\|_{2}^{2}$.

- Properties of the inner product.
    - Symmetry: $\langle x, y \rangle = \langle y, x \rangle$
        - Proof: $\sum_{i}{x_{i}y_{i}} = \sum_{i}{y_{i}x_{i}}$ since real multiplication commutes.
    - Bilinearity: linear in each slot, the other held fixed.
        - First slot: $\langle \alpha x + \beta y, z \rangle = \alpha \langle x, z \rangle + \beta \langle y, z \rangle$
        - Second slot: $\langle x, \alpha y + \beta z \rangle = \alpha \langle x, y \rangle + \beta \langle x, z \rangle$
        - Proof (first slot):
            - $\langle \alpha x + \beta y, z \rangle = \sum_{i}{(\alpha x_{i} + \beta y_{i})z_{i}} = \alpha\sum_{i}{x_{i}z_{i}} + \beta\sum_{i}{y_{i}z_{i}} = \alpha\langle x, z \rangle + \beta\langle y, z \rangle$
        - Second slot follows by symmetry.
    - Positive definiteness: $\langle x, x \rangle \geq 0$, with equality iff $x = 0$.
        - Proof: $\langle x, x \rangle = \sum_{i}{x_{i}^{2}} \geq 0$; sum of squares is zero iff every $x_{i} = 0$.

- The expansion trick (consequence of bilinearity + symmetry)
    - $\langle x + y, x + y \rangle = \|x\|_{2}^{2} + 2\langle x, y \rangle + \|y\|_{2}^{2}$
    - Derivation:
        - Bilinearity in slot 1: $\langle x + y, x + y \rangle = \langle x, x + y \rangle + \langle y, x + y \rangle$
        - Bilinearity in slot 2: $= \langle x, x \rangle + \langle x, y \rangle + \langle y, x \rangle + \langle y, y \rangle$
        - Symmetry collapses cross terms: $= \|x\|_{2}^{2} + 2\langle x, y \rangle + \|y\|_{2}^{2}$

- Orthogonality between two vectors
    - Definition: $x \perp y$ iff $\langle x, y \rangle = 0$.
    - Geometric meaning: $\cos\theta = 0 \implies \theta = 90°$. Orthogonal = perpendicular.
    - The zero vector is orthogonal to every vector (since $\langle 0, y \rangle = 0$).

- A vector orthogonal to a subspace
    - Definition: Let $V \subseteq \mathbb{R}^{n}$ be a subspace. Then $x \perp V$ iff $\langle x, v \rangle = 0$ for every $v \in V$.
    - Useful reduction: $x \perp V$ iff $\langle x, b_{i} \rangle = 0$ for every vector in some basis $\{b_{1}, \dots, b_{k}\}$ of $V$.
        - Proof:
            - Any $v \in V$ can be written as $v = c_{1}b_{1} + \dots + c_{k}b_{k}$.
            - By bilinearity in slot 2: $\langle x, v \rangle = c_{1}\langle x, b_{1} \rangle + \dots + c_{k}\langle x, b_{k} \rangle$.
            - If each $\langle x, b_{i} \rangle = 0$, then $\langle x, v \rangle = 0$ for all $v$.
            - Conversely, if $\langle x, v \rangle = 0$ for all $v \in V$, it holds for the basis vectors.
    - Why this matters: checking orthogonality to a subspace reduces from infinitely many conditions to finitely many (one per basis vector). This is the move that makes Theorem 2.1's condition $\langle b - Ax, Au \rangle = 0$ for all $u$ tractable — you only need to check it on the columns of $A$.

- Pythagorean theorem (Lemma 2.2 in the notes)
    - Statement: If $x \perp y$, then $\|x + y\|_{2}^{2} = \|x\|_{2}^{2} + \|y\|_{2}^{2}$.
    - Proof:
        - By the expansion trick: $\|x + y\|_{2}^{2} = \|x\|_{2}^{2} + 2\langle x, y \rangle + \|y\|_{2}^{2}$
        - Since $x \perp y$, $\langle x, y \rangle = 0$.
        - Hence $\|x + y\|_{2}^{2} = \|x\|_{2}^{2} + \|y\|_{2}^{2}$. $\blacksquare$
    - Generalization: if $x_{1}, \dots, x_{n}$ are mutually orthogonal (every pair), then
        - $\left\|\sum_{i=1}^{n}{x_{i}}\right\|_{2}^{2} = \sum_{i=1}^{n}{\|x_{i}\|_{2}^{2}}$
        - Proof: induction on $n$. Base case $n = 2$ is the theorem above. Inductive step uses that $x_{n+1}$ is orthogonal to $x_{1} + \dots + x_{n}$ (by the bilinearity argument from the subspace orthogonality reduction), then applies the $n = 2$ case.
    - Proof: Generalized Pythagorean Theorem [[THM_P_LA_0.2]]

## 1.3 Geometric Picture of Projections (Intuition)

- Setup: $V \subseteq \mathbb{R}^{m}$ is a subspace, $b \in \mathbb{R}^{m}$ is a point not in $V$.
- Claim: the unique point $p \in V$ closest to $b$ (in 2-norm) is characterized by $b - p \perp V$.
- This is the geometric content of Theorem 2.1: the least-squares solution $x^{*}$ is the one for which $Ax^{*}$ is the orthogonal projection of $b$ onto $\text{range}(A)$.
- The condition $\langle b - Ax, Au \rangle = 0$ for all $u \in \mathbb{R}^{n}$ is the algebraic statement of "$b - Ax$ is perpendicular to $\text{range}(A)$."
- Picture: $b$ outside the plane $V$, drop a perpendicular to land at $p \in V$. The error $b - p$ sticks straight up out of $V$.
--- 

