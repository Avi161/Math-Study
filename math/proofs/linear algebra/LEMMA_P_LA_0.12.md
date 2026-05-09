# The Identity $\langle x, A^T A x \rangle = \|Ax\|_2^2$

**Statement:** For $A \in \mathbb{R}^{m \times n}$ and $x \in \mathbb{R}^n$:
$$\langle x, A^T A x \rangle = \|A x\|_2^2.$$

**Prerequisite:** The lemma $\langle u, A^T v \rangle = \langle A u, v \rangle$ (see [[LEMMA_P_LA_0.11]]).

**Proof:**
$$\langle x, A^T A x \rangle 
\;\overset{(1)}{=}\; \langle A x, A x \rangle 
\;\overset{(2)}{=}\; \|A x\|_2^2.$$

*Justifications:*

(1) Group $A^T A x$ as $A^T (A x)$ and apply the prerequisite lemma with $u = x$ and $v = A x$:
$$\langle x, A^T (A x) \rangle = \langle A x, A x \rangle.$$

(2) By definition of the 2-norm, for any $w \in \mathbb{R}^m$:
$$\|w\|_2^2 = \sum_{i=1}^{m} w_i^2 = w^T w = \langle w, w \rangle.$$
Setting $w = A x$ gives $\langle A x, A x \rangle = \|A x\|_2^2$. $\blacksquare$

---

**Why it matters:** This identity converts a quadratic form involving $A^T A$ into a squared norm involving $A$. It's the key step in:
- Proving $A^T A$ is nonsingular iff $A$ has full column rank.
- Proving $A^T A$ is positive (semi-)definite.
- Many least-squares manipulations.