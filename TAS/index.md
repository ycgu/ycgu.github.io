---
layout: default
title: Thickness-Averaging Simulation (TAS)
---

# Thickness-Averaging Simulation

**Thickness-Averaging Simulation** (TAS) is a framework developed for accelerating SOFC numerical simulation, which involves some properties of multiscale analysis.

![This is an image](https://pic1.zhimg.com/v2-981dd6300409dddb308af401857fc05c_1440w.png?source=d16d100b)
<div style="text-align: center; color: grey; opacity: 0.8;">Schematic diagram of TAS.</div>

___

$$
\left\langle\phi\left(x,y,t\right)\right\rangle:=\int\!\!\!\int\!\!\!\int\!\!\!\int_{\Omega\times[0,T]}\mathscr G\left(x,y,z,t,\xi,\eta,\zeta,\tau\right)\phi\left(\xi,\eta,\zeta,\tau\right)d\xi d\eta d\zeta d\tau \tag{0-1}
$$
$$
\phi\left(x,y,z,t\right)=\left\langle\phi\left(x,y,t\right)\right\rangle+\widetilde\phi\left(x,y,z,t\right) \tag{0-2}
$$
