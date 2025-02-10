---
date:  '2025-02-10T16:28:09:z'
draft: false
title: 'Derivative of a matrix inverse'
tags: ["Math"]
author: ["Yuchen Gu"]
math: true
---

# Derivative of a matrix inverse
The derivative of a matrix inverse $\boldsymbol{A}^{-1}$ with respect to $\boldsymbol{A}$ is a 4th order tensor. Since $\frac{\partial}{\partial \boldsymbol{A}} \boldsymbol{A}^{-1} \boldsymbol{A} = 0$, $\frac{\partial \boldsymbol{A}^{-1}}{\partial \boldsymbol{A}} = - \boldsymbol{A}^{-2}$, but deriving its counterpart based on Einstein notation is not so obvious. Owing to,
$$
0 = \frac{\partial \delta_{km}}{\partial A_{ij}} = \frac{\partial A_{kl}^{-1}}{\partial A_{ij}} A_{lm}+A_{kl}^{-1} \frac{\partial A_{lm}}{\partial A_{ij}}
$$
and
$$
\frac{\partial A_{kn}^{-1}}{\partial A_{ij}} = \frac{\partial A_{kl}^{-1}}{\partial A_{ij}} A_{lm} A_{mn}^{-1} = - A_{kl}^{-1} \frac{\partial A_{lm}}{\partial A_{ij}} A_{mn}^{-1}
$$
where
$$
\frac{\partial A_{lm}}{\partial A_{ij}} = \delta_{li} \delta_{mj},
$$
the final expression is,
$$
\frac{\partial A_{kn}^{-1}}{\partial A_{ij}} = - A_{ki}^{-1} A_{jn}^{-1}
$$