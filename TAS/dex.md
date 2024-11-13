---
layout: default
title: Thickness-Averaging Simulation (TAS)
permalink: /TAS/
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
\left\langle\phi\left(x,y,t\right)\right\rangle:=\int\!\!\!\int\!\!\!\int\!\!\!\int_{\Omega\times[0,T]}\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right)\phi\left(\xi,\eta,\zeta,\tau\right)d\xi d\eta d\zeta d\tau \tag{1}
$$

$$
\phi\left(x,y,z,t\right)=\left\langle\phi\left(x,y,t\right)\right\rangle+\widetilde\phi\left(x,y,z,t\right) \tag{2}
$$

where $\langle \phi \rangle \in \langle V \rangle \subset \mathbb{R}^2$ and $\widetilde{\phi} \in \widetilde{V} = \langle V \rangle^\perp \subset \mathbb{R}^3$. $\mathscr{G}$ is the convolution kernel commonly used in low-pass filtering in LES derivation, based on a hybrid Box-Gaussian filter.

$$
\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right) = \frac1H\delta\left(x-\xi\right)\delta\left(y-\eta\right)\delta\left(t-\tau\right) \tag{3}
$$

Here, since the flow is laminar, we can safely use the Gaussian function with infinitely small variance $\sigma$ for $xyt$, or in other words, Dirac delta function. In the thickness direction, a box filter with filtering interval the same as layer thickness $H$ is used.

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