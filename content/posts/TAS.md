---
date:  '2024-12-09T04:56:54+09:00'
draft: true
title: 'Thickness-Averaging Simulation (TAS)'
tags: ["Math"]
author: ["Yuchen Gu"]
math: true
---

# Thickness-Averaging Simulation

**Thickness-Averaging Simulation** (TAS) is a framework developed for accelerating SOFC numerical simulation, which involves some properties of multiscale analysis.

<div style="text-align: center;">
    <img src="https://picx.zhimg.com/v2-981dd6300409dddb308af401857fc05c_1440w.png?source=d16d100b" style="max-width: 60%; height: auto;">
    <div style="color: grey; opacity: 0.8;">Schematic diagram of TAS.</div>
</div>

___

# <font size=5>*Thicknes-averaging of a function*</font>

For a fucntion $\phi \in V \subset \mathbb{R}^3$, based on direct sum decomposition $V = \langle V \rangle \oplus \widetilde{V}$, it can be decomposed as

$$
\left\langle\phi\left(x,y,t\right)\right\rangle:= \frac{\int\!\!\!\int\!\!\!\int\!\!\!\int_{\Omega\times[0,T]}\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right)\phi\left(\xi,\eta,\zeta,\tau\right) d\xi d\eta d\zeta d\tau}{\int\!\!\!\int\!\!\!\int\!\!\!\int_{\Omega\times[0,T]}\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right) d\xi d\eta d\zeta d\tau} \tag{1}
$$

$$
\phi\left(x,y,z,t\right)=\left\langle\phi\left(x,y,t\right)\right\rangle+\widetilde\phi\left(x,y,z,t\right) \tag{2}
$$

where $\langle \phi \rangle \in \langle V \rangle \subset \mathbb{R}^2$ and $\widetilde{\phi} \in \widetilde{V} = \langle V \rangle^\perp \subset \mathbb{R}^3$. $\mathscr{G}$ is the convolution kernel commonly used in low-pass filtering in LES derivation, based on a hybrid Box-Gaussian filter.

$$
\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right) = \mathcal{K} \left( x,y,t,\xi,\eta,\tau \right) \otimes \mathcal{B} \left( z, \zeta \right) \tag{3}
$$
where
$$
\mathcal{K}\left(x,y,t,\xi,\eta,\tau\right) = \frac{1}{\left( \sqrt{2\pi} \sigma \right)^3} \exp \left( - \frac{\left( x - \xi \right)^2 + \left( y - \eta \right)^2 + \left( t - \tau \right)^2}{2 \sigma^2} \right) \tag{4}
$$
and $\mathcal{B}_i \left( z, \zeta \right)$ for layer $i$ with $z \in \left[ h_i,\,h_{i+1} \right]$,
$$
\mathcal{B}_i \left( z,\zeta \right) = \left\{ 
		\begin{array}{ll}
			1, & \text{if } \zeta \in \left[ h_i,\,h_{i+1} \right] \\
			0, & \text{otherwise}
		\end{array}
	\right. \tag{5}
$$

Here, since the flow is laminar, we can safely use the Gaussian function with infinitely small variance $\sigma$ for $xyt$, or in other words, Dirac delta function. Thus, the filter becomes hybrid Box-Delta form in this case, where
$$
\lim_{\sigma \to 0} \mathcal{K}\left(x,y,t,\xi,\eta,\tau\right) = \delta\left(x-\xi\right)\delta\left(y-\eta\right)\delta\left(t-\tau\right) \tag{6}
$$

Other types of averaging technique can be defined by replacing $\mathcal{B}$ with other kernel function, which essentiially project function $\phi$ into other finite-dimensional spaces. For example, the electrical potential in SOFC electrode may look like an exponential function , for example in the form of $a_1 \exp \left( a_2 z \right)$, by minimizing the $L^2$ error, $a_1$ and $a_2$ can be solved by
$$
\begin{array}{l}
    & \int \phi\left( \zeta \right) \exp \left( a_2 \zeta \right) d\zeta = a_1 \int \exp\left( 2 a_2 \zeta \right) d\zeta \\
    & \int \phi\left( \zeta \right) \zeta \exp \left( a_2 \zeta \right) d\zeta = a_1 \int \zeta \exp\left( 2 a_2 \zeta \right) d\zeta
\end{array} \tag{7}
$$
Since the basis function is nonlinear concerning the DOFs, a general solution strategy doesn't exist.

# <font size=5>*Thicknes-averaging of an equation*</font>

Same as filtering in LES, thicknes-averaging has some properties,

$$
\left\{
   \begin{array}{ll}
    \langle\langle\phi\rangle\rangle = \langle\phi\rangle, \\
    \langle\widetilde{\phi}\rangle = 0, \\
    \langle \partial \phi / \partial \boldsymbol{x} \rangle = \partial \langle \phi \rangle / \partial \boldsymbol{x}.
   \end{array} 
   \right. \tag{4}
$$

When used in averaging an convection-diffusion-reaction equation, for example

$$
\phi_t + \boldsymbol{u}\cdot\nabla\phi - k \Delta \phi + \sigma\phi = 0 \tag{5} 
$$

$$
\Rightarrow {\langle\phi\rangle}_t + \langle\boldsymbol{u}\rangle\cdot\nabla\langle\phi\rangle - k\Delta_2\langle\phi\rangle + \sigma\langle\phi\rangle + \langle\widetilde{\boldsymbol{u}}\cdot\nabla\widetilde{\phi}\rangle - k \left. \phi_{,z} \right \vert_0^H/H = 0 \tag{6}
$$

Then subtract the averaged equation (6) from the primitive equation (5),

$$
\begin{array}{ll}
    \widetilde{\phi}_t + \widetilde{\boldsymbol{u}}\cdot\nabla\langle\phi\rangle + \langle\boldsymbol{u}\rangle\cdot\nabla\widetilde{\phi} + \widetilde{\boldsymbol{u}}\cdot\nabla\widetilde{\phi} - \langle\widetilde{\boldsymbol{u}}\cdot\nabla\widetilde{\phi}\rangle - k \Delta \widetilde{\phi} \\
    + k \left. \phi_{,z} \right \vert_0^H/H +\sigma \widetilde{\phi} = 0 \tag{7}
\end{array}
$$

The above steps are unconditionally valid without any assumptions introduced. Equation (7) has a sub-grid solution as a function of $x,\,y,\,z$ and $t$, which acts as a source of nonlocality effect after plugged into equaiton (6). For the sake of finding a prameterization of $\widetilde{\phi}$ with $\langle\phi\rangle$, multiple methods can be used, among which the most interesting one is PINN, just like what they did in turbulence closure.

>$\widetilde{\phi}_t$: Sub-grid temporal derivative
> 
>$\langle\widetilde{\boldsymbol{u}}\cdot\nabla\widetilde{\phi}\rangle$: Reynolds stress
>
>$\widetilde{\boldsymbol{u}}\cdot\nabla\langle\phi\rangle$ and $\langle\boldsymbol{u}\rangle\cdot\nabla\widetilde{\phi}$: Cross stress
>
>$k\Delta\widetilde{\phi}$: Sub-grid diffusion
>
>$k \left. \phi_{,z} \right \vert_0^H/H$: Boundary diffusive flux
>
>$\sigma\widetilde{\phi}$: Sub-grid reaction

# <font size=5>*Approximate sub-grid solution*</font>