# Generalized Pythagorean Theorem

**Theorem.** Let $x_{1}, x_{2}, \dots, x_{n} \in \mathbb{R}^{m}$ be a collection of mutually orthogonal vectors; that is, $\langle x_{i}, x_{j} \rangle = 0$ whenever $i \neq j$. Then
$$\left\| \sum_{i=1}^{n} x_{i} \right\|_{2}^{2} = \sum_{i=1}^{n} \|x_{i}\|_{2}^{2}.$$

**Proof.** We proceed by induction on $n$.

For the base case $n = 2$, suppose $x_{1}, x_{2}$ satisfy $\langle x_{1}, x_{2} \rangle = 0$. Expanding via the bilinearity and symmetry of the inner product,
$$\|x_{1} + x_{2}\|_{2}^{2} = \langle x_{1} + x_{2},\, x_{1} + x_{2} \rangle = \langle x_{1}, x_{1} \rangle + 2\langle x_{1}, x_{2} \rangle + \langle x_{2}, x_{2} \rangle = \|x_{1}\|_{2}^{2} + \|x_{2}\|_{2}^{2},$$
where the final equality uses $\langle x_{1}, x_{2} \rangle = 0$.

Now suppose, for the inductive hypothesis, that the result holds for some $k \geq 2$; that is, for any mutually orthogonal collection $\{y_{1}, \dots, y_{k}\}$,
$$\left\| \sum_{i=1}^{k} y_{i} \right\|_{2}^{2} = \sum_{i=1}^{k} \|y_{i}\|_{2}^{2}.$$

Let $\{x_{1}, \dots, x_{k+1}\}$ be a mutually orthogonal collection, and define $S_{k} := \sum_{i=1}^{k} x_{i}$. By bilinearity of the inner product in the first argument,
$$\langle S_{k}, x_{k+1} \rangle = \left\langle \sum_{i=1}^{k} x_{i},\, x_{k+1} \right\rangle = \sum_{i=1}^{k} \langle x_{i}, x_{k+1} \rangle = 0,$$
since each summand vanishes by hypothesis. Hence $S_{k} \perp x_{k+1}$, and applying the base case to the pair $(S_{k}, x_{k+1})$ yields
$$\left\| \sum_{i=1}^{k+1} x_{i} \right\|_{2}^{2} = \|S_{k} + x_{k+1}\|_{2}^{2} = \|S_{k}\|_{2}^{2} + \|x_{k+1}\|_{2}^{2}.$$

By the inductive hypothesis, $\|S_{k}\|_{2}^{2} = \sum_{i=1}^{k} \|x_{i}\|_{2}^{2}$, and therefore
$$\left\| \sum_{i=1}^{k+1} x_{i} \right\|_{2}^{2} = \sum_{i=1}^{k} \|x_{i}\|_{2}^{2} + \|x_{k+1}\|_{2}^{2} = \sum_{i=1}^{k+1} \|x_{i}\|_{2}^{2}.$$

The result follows by induction. $\blacksquare$
