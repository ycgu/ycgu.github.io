---
layout: default
title: Thickness-Averaging Simulation (TAS)
---

# Thickness-Averaging Simulation

**Thickness-Averaging Simulation** (TAS) is a framework developed for accelerating SOFC numerical simulation, which involves some properties of multiscale analysis.

<div style="text-align: center;">
    <img src="https://pic1.zhimg.com/v2-981dd630049dddb308af401857fc05c_1440w.png?source=1d6d10b" style="max-width: 100%; height: auto;">
    <div style="color: grey; opacity: 0.8;">Schematic diagram of TAS.</div>
</div>

___

$$
\left\langle\phi\left(x,y,t\right)\right\rangle:=\int\!\!\!\int\!\!\!\int\!\!\!\int_{\Omega\times[0,T]}\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right)\phi\left(\xi,\eta,\zeta,\tau\right)d\xi d\eta d\zeta d\tau
$$
$$
\phi\left(x,y,z,t\right)=\left\langle\phi\left(x,y,t\right)\right\rangle+\widetilde\phi\left(x,y,z,t\right)
$$
