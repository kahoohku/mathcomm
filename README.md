# Test

--

## Riesz Representation Theorems

**Riesz Representation Theorem.**
Suppose $V$ is a finite-dimensional inner-product space and $\varphi$ is a linear functional on $V$.
Then there is a unique vector $v \in V$ such that
\[ \varphi u = \langle u, v \rangle, \qquad \text{for all } u \in V. \]

**Riesz Representation Theorem.**
Let $H$ be a Hilbert space.
For every continuous linear functional $\varphi \in H^*$, there is a unique vector $v \in H$ such that
\[ \varphi u = \langle u, v \rangle, \qquad \text{for all } u \in H. \]
Moreover, $\norm v = \norm \varphi$.

**Riesz Representation Theorem.**
Suppose $X$ is a $\sigma$-compact LCH space and $I$ is a positive linear functional on $C_c(X)$.
Then there is a unique regular Borel measure $\mu$ on $X$ such that $I(f) = \int f\, d\mu$ for all $f \in C_c(X)$.
Moreover, $\mu$ satisfies
\[ \mu(U) = \sup\{ I(f) : f \in C_c(U), 0 \leq f \leq 1 \} \]
and
\[ \mu(K) = \inf\{ I(f) : f \in C_c(X), f \geq \chi_K \]
for all open $U$ and compact $K$.

**Riesz Representation Theorem.**
Suppose $\mu$ is $\sigma$-finite, $1 \leq p < \infty$, and $p$, $q$ are conjugate exponents.
The map $\varphi \colon L^q \to (L^p)^*$ given by
\[ g \mapsto \varphi_g, \quad \varphi_g(f) = \int \!\! fg\, d\mu \]
is a bijective isometry. In particular, $L^p$ is reflexive for $1 < p < \infty$.

