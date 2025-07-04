---
layout: page
title: Green's function for advection-wave equation
description: Green's function for wave equation with advection in 1D infinite domain
importance: 1
date: 2025-07-04 12:30:00-0400
category: Physics
---


In its general form, the advection-wave equation of a scalar field $$p(\mathbf{r})$$ reads

$$\frac{\partial^2 p}{\partial t^2} + 2 \mathbf{u} \cdot \nabla \frac{\partial p}{\partial t} - a \nabla\cdot (b\nabla p) = f$$

It is a second-order (in time and space) linear partial differential equation (PDE) in $$p$$. Here I only look at the homogeneous case, where $$a$$ and $$b$$ are merely constants. In this case we have

$$\frac{\partial^2 p}{\partial t^2} + 2 \mathbf{u} \cdot \nabla \frac{\partial p}{\partial t} - c^2 \nabla^2 p = f$$

where $$c$$ is the wave speed.

# Green's function for 1D advection-wave equation in infinite domain

The equation in 1D reads

$$\frac{\partial^2 p}{\partial t^2} + 2 v \frac{\partial^2 p}{\partial x \partial t} - c^2 \frac{\partial^2 p}{\partial x^2} = f$$

The corresponding problem for the Green's function $$g(x, t; x', t')$$ is

$$\begin{aligned}
    &\text{Equation:}\quad & &\frac{\partial^2 g}{\partial t^2} + 2 v \frac{\partial^2 g}{\partial x \partial t} - c^2 \frac{\partial^2 g}{\partial x^2} = \delta(t-t') \delta(x-x') \\[5pt] 
    &\text{Initial condition:}\quad & &g|_{t<t'} = 0, \quad \partial_t g|_{t<t'} = 0 \\[8pt]
    &\text{Boundary condition:}\quad & &g|_{x\rightarrow +\infty} = 0, \quad g|_{x\rightarrow -\infty} = 0
\end{aligned}$$

In the situation where $$v < c$$, the Green's function can be solved to be

$$\begin{aligned}
    g(x,t;x',t') &= \frac{H(t-t')}{2\sqrt{c^2 + v^2}} \left[H\left(t-t' - \frac{x - x'}{\sqrt{c^2 + v^2} + v}\right) + H\left(t-t' + \frac{x - x'}{\sqrt{c^2 + v^2} - v}\right) - 1\right] \\ 
    &= \frac{H(t-t')}{2\sqrt{c^2 + v^2}} \, \mathbb{1} \left(-(\sqrt{c^2 + v^2} - v) < \frac{x - x'}{t - t'} < \sqrt{c^2 + v^2} + v\right)
\end{aligned}$$

where $$H(\cdot)$$ is the Heaviside step function, taking value of $$1$$ when argument $$> 0$$ and otherwise zero, and $$\mathbb{1}(\cdot)$$ is the indicator function, taking value of $$1$$ when the argument condition is satisfied, otherwise zero. If we introduce Mach number

$$\mathrm{M} = \frac{v}{c} < 1$$

The Green's function can be rewritten as

$$\begin{aligned}
    g(x,t;x',t') &= \frac{H(t-t')}{2c\sqrt{1 + \mathrm{M}^2}} \left[H\left(t-t' - \frac{x - x'}{c(\sqrt{1 + \mathrm{M}^2} + \mathrm{M})}\right) + H\left(t-t' + \frac{x - x'}{c(\sqrt{1 + \mathrm{M}^2} - \mathrm{M})}\right) - 1\right] \\ 
    &= \frac{H(t-t')}{2c\sqrt{1 + \mathrm{M}^2}} \, \mathbb{1} \left(-c(\sqrt{1 + \mathrm{M}^2} - \mathrm{M}) < \frac{x - x'}{t - t'} < c(\sqrt{1 + \mathrm{M}^2} + \mathrm{M})\right).
\end{aligned}$$

The interpretation of this 1D Green's function is very straightforward. The pertubation at time $$t'$$ and position $$x'$$ will travel upwind (=against the advection direction) with a velocity $$\sqrt{c^2 + v^2} - v = c (\sqrt{1 + \mathrm{M}^2} - \mathrm{M})$$ slightly greater than the wave speed, and downwind (=following the advection direction) with a velocity $$\sqrt{c^2 + v^2} + v = c (\sqrt{1 + \mathrm{M}^2} + \mathrm{M})$$, slightly lower than the wave speed. The propagation of the pertubation in both direction takes the form of a step function, with a constant amplitude $$1/(2\sqrt{c^2 + v^2}) = 1/(2c\sqrt{1 + \mathrm{M}^2})$$. I leave the derivation in the back.

## Zeroth-order approximation

At Mach number $$\mathrm{M} = 0$$, the system degenerates to the original wave equation with no advection; the Green's function can be immediately obtained by setting $$\mathrm{M} = 0$$ in the expression above:

$$\begin{aligned}
    g(x,t;x',t') &= \frac{H(t-t')}{2c} \left[H\left(t-t' - \frac{x - x'}{c}\right) + H\left(t-t' + \frac{x - x'}{c}\right) - 1\right] \\ 
    &= \frac{H(t-t')}{2c} \, \mathbb{1} \left(-c < \frac{x - x'}{t - t'} < c\right).
\end{aligned}$$

## First-order approximation

At Mach number $$\mathrm{M} \ll 1$$, $$\sqrt{1 + \mathrm{M}^2} \sim 1 + \frac{1}{2} \mathrm{M}^2$$, and hence only deviates from $$1$$ by a second-order term. If we keep only the first-order terms, then

$$\begin{aligned}
    g(x,t;x',t') &= \frac{H(t-t')}{2c} \left[H\left(t-t' - \frac{x - x'}{c + v}\right) + H\left(t-t' + \frac{x - x'}{c - v}\right) - 1\right] \\ 
    &= \frac{H(t-t')}{2c} \left[H\left(t-t' - \frac{x - x'}{c(1 + \mathrm{M})}\right) + H\left(t-t' + \frac{x - x'}{c(1 - \mathrm{M})}\right) - 1\right] \\ 
    &= \frac{H(t-t')}{2c} \, \mathbb{1} \left(-(c - v) < \frac{x - x'}{t - t'} < c + v\right) \\ 
    &= \frac{H(t-t')}{2c} \, \mathbb{1} \left(-c(1 - \mathrm{M}) < \frac{x - x'}{t - t'} < c(1 + \mathrm{M})\right)
\end{aligned}$$

At this order the pertubations simply propagate at speeds $$c + v$$ and $$c - v$$ in each direction. It should however be noted that here the approximation in the propgation velocity has been used. This approximation is not uniformly valid at large distance / long propgation time, but only up to a certain distance / time that scales with $$\mathrm{M}^{-1}$$.

## Derivation of the Green's function

Here I follow what I believe is a relatively rigorous route to derive the Green's function. Only key steps are shown. In accordance with the infinite domain and the boundary condition at $$\pm \infty$$, we can Fourier transform the PDE into the wavenumber domain

$$\mathscr{F}[\cdot]: \quad \mapsto \quad \frac{\partial^2 \tilde{g}}{\partial t^2} + 2ikv \frac{\partial \tilde{g}}{\partial x} + k^2 c^2 \tilde{g} = \frac{e^{-ikx'}}{\sqrt{2\pi}} \delta(t - t')$$

where

$$\tilde{g}(k,t;x',t) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{+\infty} g(x,t;x',t') e^{-ikx} \, dx$$

is the Fourier transformed Green's function in wavenumber domain. Now the PDE is converted to an ODE initial value problem (IVP). The solution to this problem reads

$$\tilde{g}(k,t;x',t) = \frac{e^{-ikx'}}{k\sqrt{2\pi (c^2 + v^2)}} e^{-ikv(t - t')} \sin \left(k\sqrt{c^2 + v^2} (t - t')\right) H(t-t')$$

The final step is then to convert this back to space domain using an inverse Fourier transform

$$\begin{aligned}
    g(x,t;x',t') &= \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{+\infty} \tilde{g}(k,t;x',t) \, e^{ikx} dk \\
    &= \frac{H(t - t')}{2\pi \sqrt{c^2 + v^2}} \int_{-\infty}^{+\infty} \sin \left(k\sqrt{c^2 + v^2} (t - t')\right) \exp\left(-ikv\left(t - t' - \frac{x - x'}{v}\right)\right) \, \frac{dk}{k}
\end{aligned}$$

This can be written as a combination of $$\int_\mathbb{R} \frac{e^{ipk}}{k}dk$$ integrals and evaluated using the residual theorem and Jordan's lemma. Evaluation of this integral yields the answer.


