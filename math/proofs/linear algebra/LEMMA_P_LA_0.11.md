# Moving a Matrix Across the Inner Product

**Statement:** For $A \in \mathbb{R}^{m \times n}$, $u \in \mathbb{R}^n$, and $v \in \mathbb{R}^m$:
$$\langle u, A^T v \rangle = \langle A u, v \rangle.$$

Equivalently (swapping roles): $\langle A u, v \rangle = \langle u, A^T v \rangle$.

**Setup:** The standard inner product on $\mathbb{R}^k$ is $\langle x, y \rangle = x^T y$.

**Proof:**
$$\langle u, A^T v \rangle = u^T (A^T v) = (u^T A^T) v = (A u)^T v = \langle A u, v \rangle.$$
$\blacksquare$

---

*Justifications:*
- 1st equality: definition of inner product.
- 2nd equality: associativity of matrix multiplication.
- 3rd equality: $(AB)^T = B^T A^T$ applied with $B = u$ (treating $u$ as an $n \times 1$ matrix), giving $(A u)^T = u^T A^T$.
- 4th equality: definition of inner product. $\blacksquare$

**Why it matters:** This is the workhorse identity for almost every proof involving $A^T A$ or $A A^T$. Whenever you see one of these "sandwich" expressions in an inner product, this lemma lets you split the matrix to one side.