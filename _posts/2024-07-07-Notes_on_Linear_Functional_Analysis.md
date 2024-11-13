---
layout: post
title: "My Research Note on Linear Functional Analysis"
date: 2023-07-01
---

# The Orthogonal Decomposition Theorem

---

Let $V$ be a Hilbert space and $M\subset V$ a closed subspace of $V$. Then
(i) $M^\bot$ is a closed subspace of $V$.
(ii) $V$ can be represented as the direct sum of $M$ and its orthogonal complement $M^\bot$

$$
V=M\oplus M^\bot
$$

i.e., every vector $v\in V$ can be uniquely decomposed into two orthogonal vectors $\boldsymbol m$, $\boldsymbol n$, s.t.

$$
\boldsymbol v=\boldsymbol m+\boldsymbol n, \boldsymbol m\in M,\boldsymbol n\in M^\bot
$$

**COROLLARY**
Let $V$ be a Hilbert space and $M$ a vector subspace of $V$ . The following conditions are equivalent to each other
(i) $M$ is closed.
(ii) $(M^\bot)^\bot = M$.

# Orthogonal projection
Let $M$ be a closed subspace of a Hilbert space $V$. The linear projection $P_M$ corresponding to the decomposition

$$
V=M\oplus M^\bot, \boldsymbol v=\boldsymbol m+\boldsymbol n
$$ 

and prescribing for any vector $\boldsymbol v$ its $\boldsymbol m$ component
$$
P_M:V\to V, P_M\boldsymbol v=\boldsymbol m
$$
is called the orthogonal projection onto the subspace $M$ s.t. $\parallel P_M\parallel=1$ (unit norm).

# Riesz Representation Theorem
Let $V$ be a Hilbert space and let $f$ be a continuous linear functional on $V$. Then there exists a unique element $\boldsymbol u\in V$ such that
$$
f(\boldsymbol v) = (\boldsymbol v,\boldsymbol u),\;\forall \boldsymbol v\in V
$$
where $\left(\cdot,\cdot\right)$ is the scalar product on $V$. Moreover,
$$
\| f\|_{V\prime} =\|\boldsymbol u\|_V
$$

## COROLLARY
Let $R: V\to V\prime$ denote the map from a Hilbert space $V$ onto its dual $V\prime$ such that
$$
\langle R\boldsymbol u,\boldsymbol v\rangle= (\boldsymbol u,\boldsymbol v),\;\forall \boldsymbol u,\boldsymbol v\in V
$$
Then:
(i) $R$ is an **antilinear** map from $V$ onto $V\prime$.
(ii) $R$ preserves the norm, i.e.,
$$
\|R\boldsymbol u\|_{V\prime} = \|\boldsymbol u\|_V
$$
In particular, in the case of a real Hilbert space $V$ , $R$ is a linear norm-preserving isomorphism (surjective isometry) from $V$ onto $V\prime$. $R$ is also known as ***Riesz*** map to identify the topological dual of $V$ with itself.

Applying the Riesz representation theorem to the dual space $V\prime$, we can introduce the Riesz map for the dual space as
$$
R_{V\prime}:V\prime\ni g\to\{f\to(f,g)_{V\prime}\in\mathbb{C}\}\in(V\prime)\prime
$$
where$(V\prime)\prime$ is the bidual of $V$.

# Adjoint of a Continuous Operator
Let $U$, $V$, $W$ be inner product spaces and let $A$, $A_i\in\mathcal L(U,V), i = 1,2$, and $B\in \mathcal L(V,W)$. The following properties hold.
(i) Adjoint of a linear combination of operators is equal to the linear combination of the corresponding adjoint operators with complex conjugate coefficients
$$
(\alpha_1A_1 + \alpha_2A_2)^\ast =\overline\alpha_1A^\ast_1 + \overline\alpha_2A^\ast_2
$$
(ii) Adjoint of a composition is equal to the composition of the adjoint operators with inverted order
$$
(B\circ A)^\ast = A^\ast\circ B^\ast
$$
(iii) Adjoint of the identity operator equals the operator itself
$$
(id_U )^\ast = id_U
$$
(iv) If the inverse $A^{−1}$ exists and is continuous then $A^\ast$ has a continuous inverse too, and
$$
(A^\ast)^{−1} = (A^{−1})^\ast
$$
(v) Norm of the adjoint equals norm of the operator
$$
\|A\|_{\mathcal L(U,V )} = \|A^\ast\|_{\mathcal L(V,U)}
$$
(vi) Adjoint of the adjoint coincides with the original operator
$$
(A^\ast)^\ast = A
$$

# Symmetric and Self-Adjoint Operators. 
An operator $A$ defined on a dense subspace $D(A)$ of a Hilbert space $U$ into itself is said to be symmetric, if $A\subset A^\ast$, i.e.,
$$
D(A)\subset D(A^\ast) \;and\; A^\ast|_{D(A)} = A
$$
If, additionally, the domains of both operators are the same, i.e., $A = A^\ast$, then we say that operator $A$ is self-adjoint. Obviously, every self-adjoint operator is symmetric, but not conversely. In the case of a continuous and symmetric operator $A$ defined on the whole space $U$, however, the adjoint $A^\ast$ is defined on the whole $U$ as well, and, therefore, $A$ is automatically self-adjoint.

## Example
Orthogonal projections in a Hilbert space are self-adjoint. Indeed, let $M$ be a closed subspace of a Hilbert space $V$ and $P$ the corresponding orthogonal projection on $M$, i.e., if
$$
\boldsymbol u=\boldsymbol u_1+\boldsymbol u_2\; where\; \boldsymbol u_1\in M,\boldsymbol u_2\in M^\bot
$$
then $P\boldsymbol u=\boldsymbol u_1$. Similarly, $P\boldsymbol v=\boldsymbol v_1,\;for\; \boldsymbol v=\boldsymbol v_1+\boldsymbol v_2, \boldsymbol v_1\in M, \boldsymbol v_2\in M^\bot$. We have
$$
(P\boldsymbol u,\boldsymbol v)=(\boldsymbol u_1,\boldsymbol v)=(\boldsymbol u_1,\boldsymbol v_1 +\boldsymbol v_2)= (\boldsymbol u_1,\boldsymbol v_1) = (\boldsymbol u_1 +\boldsymbol u_2,\boldsymbol v_1) = (\boldsymbol u,\boldsymbol v_1) = (\boldsymbol u,P\boldsymbol v)
$$
for every $\boldsymbol u, \boldsymbol v\in V$.

# Some norms in Soblev Spaces
Classical $H^1$ Sobolev space consisting of all $L^2$-functions whose distributional derivatives are also functions, and they are $L^2$-integrable as well,
$$
H^1(\Omega) :=\{u\in L^2(\Omega) : \dfrac{\partial u}{\partial x_i} \in L^2(\Omega), i = 1,\;\cdots,N\}
$$
The space is equipped with the norm,
$$
\|u\|_{H^1}^2 :=\|u\|^2 + \sum_{i=1}^N\|\dfrac{\partial u}{\partial x_i}\|^2
$$
where $\| \cdot \|$ denotes the $L^2$-norm. The second term constitutes a seminorm on $H^1(\Omega)$ and will be denoted by
$$
|u|^2_{H_1}:= \sum_{i=1}^N \|\dfrac{\partial u}{\partial x_i}\|^2
$$
The second space, $H(div,\Omega)$, consists of all vector-valued $L^2$-integrable functions whose distributional divergence is also a function, and it is $L^2$-integrable,
$$
H(div, \Omega) := \{\boldsymbol\sigma = (\sigma_i)^N_{i=1} \in (L^2(\Omega))^N : div\;\boldsymbol\sigma \in L^2(\Omega)\}
$$
The space is equipped with the norm,
$$
\|\boldsymbol\sigma\|^2_{H(div)} := \|\boldsymbol\sigma\|^2 + \|div\;\boldsymbol\sigma\|^2
$$
where the $L^2$-norm of vector-valued functions is computed componentwise,
$$
\|\boldsymbol\sigma\|^2 := \sum_{i=1}^N \|\sigma_i\|^2
$$

## Example
The classical integration by parts formula generalizes to the energy spaces,
$$
(\boldsymbol\sigma,\nabla u)=−(div\;\boldsymbol\sigma,u)+\langle\sigma_n,u\rangle, \boldsymbol\sigma\in H(div,\Omega),u\in H_1(\Omega)
$$
The brackets $\langle\cdot,\cdot\rangle$ denote the duality pairing between $H^{1/2}(\Gamma)$ and $H^{−1/2}(\Gamma)$ (topological dual of each other) that generalizes the usual integral over the boundary.

Since boundary conditions are imposed by trace operators, we will need the following subspaces of the energy spaces,
$$
H^1_{\Gamma_1} (\Omega):=\{u\in H^1(\Omega) : u=0\;on\;\Gamma_1\}
$$
$$
H_{\Gamma_2}(div,\Omega):=\{\boldsymbol\sigma\in H(div,\Omega) : \sigma_n =0\;on\;\Gamma_2\}
$$

As for regular functions, we have
$$
(\boldsymbol\sigma,\nabla u)=−(\nabla\cdot\boldsymbol\sigma,u)\;\boldsymbol\sigma\in H_{\Gamma_2}(div,\Omega),u\in H_{\Gamma_1}^1 (\Omega)
$$

# Variational formulation for diffusion-convection-reaction eqaution
$$
\left\{\begin{array}{ll}
u\in H^1_{\Gamma_1}(\Omega) \\[2ex]
\displaystyle{\int_\Omega}(a_{ij}u_{,j}v_{,i} − b_iuv_{,i} + cuv) = {\int_\Omega} fv \;\;\;v\in H_{\Gamma_1}^1 (\Omega)
\end{array}\right.
$$

***Note***: The convection term is also integrated by parts here to avoid integrable requirement for high-order derivative of $b$.

## Poincaré Inequality
There exists a positive constant $c > 0$ such that
$$
c\|u\|^2 \leq |u|^2_{H^1}
$$
for all $u \in H^1(\Omega)$ that vanish on $\Gamma_1$.

## Lax-Milgram theorem
Let $X$ be a Hilbert space with a closed subspace $V$ and let $b : X\times X \to \mathbb{R}\;(or\;\mathbb{C})$ be a sesquilinear continuous form that is V-coercive (some authors say V-elliptic), i.e., a constant $\alpha > 0$ exists such that
$$
|b(v,v)| \geq \alpha\|v\|^2_X\;\;\; \forall v \in V
$$
Then, for every antilinear and continuous functional $l$ on $V$, $l \in V\prime$, and element $\widetilde u_0 \in X$, there exists a unique solution to the abstract variational problem
$$
\left\{\begin{array}{ll}
Find\;u\in\widetilde  u_0+V\;such\;that \\[2ex]
b(u,v) = l(v) \;\;\;\forall v \in V
\end{array}\right.
$$
The solution u depends continuously on the data,
$$
\|u\|\leq\dfrac1\alpha \| l \| _{V\prime} +( \dfrac M\alpha + 1) \|\widetilde u_0 \|_X
$$
