# $A^T A$ is Nonsingular $\iff$ $A$ has Full Column Rank

**Statement:** Let $A \in \mathbb{R}^{m \times n}$ with $m \geq n$. Then
$$A^T A \text{ is nonsingular} \iff A \text{ has full column rank}.$$

**Prerequisite:** The identity $\langle x, A^T A x \rangle = \|A x\|_2^2$ (see [[LEMMA_P_LA_0.12]]).

**Background facts used:**
- A square matrix $M$ is nonsingular $\iff$ $\ker(M) = \{0\}$, where $\ker(M) = \{x : M x = 0\}$.
- $A$ has full column rank $\iff$ its columns are linearly independent $\iff$ $\ker(A) = \{0\}$.
- $A^T A \in \mathbb{R}^{n \times n}$ is square.

## Strategy

Reduce the equivalence to a single claim about kernels:
$$\ker(A^T A) = \ker(A).$$

Once this is established:
$$A^T A \text{ nonsingular} \iff \ker(A^T A) = \{0\} \iff \ker(A) = \{0\} \iff A \text{ has full column rank}. \quad\blacksquare$$

## Proof of the claim: $\ker(A^T A) = \ker(A)$

We prove the two inclusions separately.

**($\ker(A) \subseteq \ker(A^T A)$):** Suppose $x \in \ker(A)$, so $A x = 0$. Then
$$A^T A x = A^T (A x) = A^T \cdot 0 = 0,$$
so $x \in \ker(A^T A)$.

**($\ker(A^T A) \subseteq \ker(A)$):** Suppose $x \in \ker(A^T A)$, so $A^T A x = 0$. Take the inner product with $x$:
$$\langle x, A^T A x \rangle = \langle x, 0 \rangle = 0.$$

By the prerequisite identity, $\langle x, A^T A x \rangle = \|A x\|_2^2$, so
$$\|A x\|_2^2 = 0.$$

A norm is zero only at the zero vector, so $A x = 0$, i.e. $x \in \ker(A)$. $\blacksquare$

## Why it matters

This is the fact that makes the normal equations $A^T A x = A^T b$ uniquely solvable in the full-rank least-squares problem (Theorem 2.1 in the notes). Without full column rank, $A^T A$ is singular and the least-squares solution is not unique — which is exactly the situation handled later by the SVD (Section 5.3).