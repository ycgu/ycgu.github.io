---
date:  '2025-02-10T17:22:13+09:00'
draft: false
title: 'Derivative of a matrix inverse'
tags: ["Math"]
author: ["Yuchen Gu"]
math: true
---

# Derivative of a matrix inverse

The derivative of a matrix inverse $\boldsymbol{A}^{-1}$ with respect to $\boldsymbol{A}$ is a 4th order tensor. Since $\dfrac{\partial}{\partial \boldsymbol{A}} \left( \boldsymbol{A}^{-1} \boldsymbol{A} \right) = 0$, $\dfrac{\partial \boldsymbol{A}^{-1}}{\partial \boldsymbol{A}} = - \boldsymbol{A}^{-2}$, but deriving its counterpart based on Einstein notation is not so obvious. Owing to,

$$
0 = \frac{\partial \delta_{km}}{\partial A_{ij}} = \frac{\partial A_{kl}^{-1}}{\partial A_{ij}} A_{lm}+A_{kl}^{-1} \frac{\partial A_{lm}}{\partial A_{ij}}
$$

and

$$
\frac{\partial A_{kn}^{-1}}{\partial A_{ij}} = \frac{\partial A_{kl}^{-1}}{\partial A_{ij}} A_{lm} A_{mn}^{-1} = - A_{kl}^{-1} \frac{\partial A_{lm}}{\partial A_{ij}} A_{mn}^{-1},
$$

where

$$
\frac{\partial A_{lm}}{\partial A_{ij}} = \delta_{li} \delta_{mj},
$$

the final expression is,

$$
\frac{\partial A_{kn}^{-1}}{\partial A_{ij}} = - A_{ki}^{-1} A_{jn}^{-1}
$$

The first order derivative can be expressed as $\mathbb{A}^{(1)}_{ijkl} = - A_{ik}^{-1} A_{lj}^{-1}$, for second order derivative, $\dfrac{\partial^2 \boldsymbol{A}^{-1}}{\partial \boldsymbol{A}^2} = 2 \boldsymbol{A}^{-3}$, the formula for Einstein notation is,

$$
\mathbb{A}^{(2)}_{ijklpq} = - \frac{\partial A_{ik}^{-1}}{\partial A_{pq}} A_{lj}^{-1} - A_{ik}^{-1} \frac{\partial A_{lj}^{-1}}{\partial A_{pq}} = A_{ip}^{-1} A_{qk}^{-1} A_{lj}^{-1} + A_{ik}^{-1} A_{lp}^{-1} A_{qj}^{-1}
$$

Similar results can be derived for higher order derivatives.