---
layout: page
title: Diffusion on poloidal and toroidal vector fields
description: Poloidal fields and toroidal fields are invariant function spaces under magnetic diffusion, even with radially varying diffusivity
importance: 1
date: 2024-03-24 12:00:00-0400
category: Physics
---

In this note I shall review the the effect of diffusion operator operated on poloidal and toroidal vector fields. In particular, I will investigate a scheme that is relevant to Earth and planetary fluid dynamics: the viscous/magnetic diffusion with radially varying diffusivity, and how the poloidal and toroidal fields are converted under these operators.

---
## Diffusion operators

The ***viscous diffusion*** term in Navier Stokes equation reads

$$
D_\nu = \frac{1}{\rho} \nabla\cdot (\mu \nabla \mathbf{v})
$$

where $$\mu$$ is the dynamic viscosity, and $$\mathbf{v}$$ the velocity. In this note I shall assume incompressibility of the fluid, such that $$\nabla\cdot \mathbf{v} = 0$$, and there is a toroidal-poloidal decomposition of the solenoidal field (see e.g. [[Vector Representation]]). When assuming uniform viscosity, this term is just scaled Laplacian of the velocity field

$$
D_\nu = \frac{\mu}{\rho} \nabla^2 \mathbf{v}
$$

The ***magnetic diffusion*** term in the induction equation reads

$$
D_\eta = -\frac{1}{\mu_0} \nabla\times \left(\frac{1}{\sigma}\nabla\times \mathbf{B}\right) = -\nabla\times \left(\frac{1}{\mu_0 \sigma} \nabla\times \mathbf{B}\right) = -\nabla\times (\eta\nabla\times \mathbf{B})
$$

where $$\sigma$$ is the electrical conductivity, $$\mu_0$$ the magnetic permeability, and $$\eta$$ the magnetic diffusivity. When assuming uniform diffusivity (as is very commonly done in geodynamo), this term is just

$$
D_\eta = -\eta \nabla\times(\nabla\times \mathbf{B}) = \eta \nabla^2 \mathbf{B}
$$

The solenoidal property of $$\mathbf{B}$$ always holds, and is already used here. In many cases, especially for giant planets or stars, diffusivity can span several orders of magnitudes at different radius, and a uniform diffusivity is no longer a valid assumption. This motivates the so-called *anelastic approximation* for the fluid flow, in contrast to the *incompressible approximation* typically used in geodynamo.

---
## Magnetic diffusion operator

**Preposition:** The magnetic diffusion operator with radially varying diffusivity, defined as 
$$
\mathcal{L}_\eta: \mathbf{A} \mapsto -\nabla\times (\eta(r) \nabla\times \mathbf{A})
$$maps a toroidal field to a toroidal field, and a poloidal field to a poloidal field. That is, introducing the space of toroidal vector fields and polidal vector fields, $$\mathcal{T}$$ and $$\mathcal{P}$$ respectively, we have

$$
\mathcal{L}_\eta \mathbf{A}\in \mathcal{T}\quad (\forall \mathbf{A}\in \mathcal{T}),\qquad
\mathcal{L}_\eta \mathbf{A}\in \mathcal{P}\quad (\forall \mathbf{A}\in \mathcal{P})
$$

In other words, **the subspaces $$\mathcal{T}$$ and $$\mathcal{P}$$ are invariant subspaces under transform $$\mathcal{L}_\eta$$.**

**Proof**: 

First, consider a poloidal field $$\mathbf{A}\in \mathcal{P}$$. Hence $$\exists P(\mathbf{r})$$ such that $$\mathbf{A} = \nabla\times (\nabla\times P(\mathbf{r})\mathbf{r})$$. The (magnetic) diffusion of a poloidal field then takes the form

$$
\mathcal{L}_\eta \mathbf{A} = \nabla\times (\eta \nabla\times \nabla\times  \nabla\times P\mathbf{r})
$$

Using the property that the curl of a poloidal field is a toroidal field (see [[Vector Representation]]), i.e.

$$
\nabla\times \nabla\times \nabla \times P\mathbf{r} = \hat{\mathbf{r}}\times \nabla_s (\nabla^2 P)
$$

and using the commutative property of $$\eta(r)$$ with $$\hat{\mathbf{r}}\times \nabla_s$$, we arrive at the expression

$$
\mathcal{L}_\eta \mathbf{A} = \nabla \times (\hat{\mathbf{r}}\times \nabla_s(\eta \nabla^2 P )) = \nabla\times \nabla\times (-\eta \nabla^2 P \, \mathbf{r}) \in \mathcal{P}
$$

Hence the resulting diffusion term is a poloidal field, with modified poloidal scalar $$-\eta \nabla^2 P$$.

If, on the other hand, $$\mathbf{A} \in \mathcal{T}$$, i.e. $$\exists \, T(\mathbf{r})$$ such that $$\mathbf{A} = \nabla\times (T(\mathbf{r}) \mathbf{r})$$, the magnetic diffusion

$$
\begin{aligned}
L_\eta \mathbf{A} &= \nabla\times (\eta \nabla\times \nabla\times T\mathbf{r}) \\
&= \frac{d\eta}{dr} \hat{\mathbf{r}}\times (\nabla\times \nabla\times T\mathbf{r}) + \eta \nabla\times (\nabla\times \nabla\times T\mathbf{r})
\end{aligned}
$$

Using again the double curls and triple curls of $$f\mathbf{r}$$ (see [[Vector Representation]]), we have

$$
\begin{aligned}
L_\eta \mathbf{A} &= \frac{d\eta}{dr}\hat{\mathbf{r}}\times \left[-\hat{\mathbf{r}} \nabla_s^2 \frac{T}{r} + \nabla_s\left(\frac{1}{r}\frac{\partial (rT)}{\partial r}\right)\right] + \eta \nabla\times (-\mathbf{r}\nabla^2T) \\
&= \frac{d\eta}{dr}\hat{\mathbf{r}} \times \nabla_s \left(\frac{1}{r}\frac{\partial (rT)}{\partial r}\right) + \eta \hat{\mathbf{r}}\times \nabla_s (\nabla^2 T)
\end{aligned}
$$

Again applying the commutative property and moving $$\eta$$ and $$d\eta/dr$$ inside the surface operators

$$
L_\eta \mathbf{A} = \hat{\mathbf{r}}\times \nabla_s \left[\frac{1}{r}\frac{d\eta}{dr}\frac{\partial (rT)}{\partial r} + \eta \nabla^2 T\right] \in \mathcal{T}
$$

Hence the resulting diffusion term is a toroidal field, with toroidal scalar $$-\eta \nabla^2 T - \frac{1}{r}\frac{d\eta}{dr}\frac{\partial (rT)}{\partial r}$$.
In summary, $$\mathcal{L}_\eta \mathbf{A} \in \mathcal{T}$$ forall $$\mathbf{A}\in \mathcal{T}$$, and $$\mathcal{L}_\eta \mathbf{A} \in \mathcal{P}$$ forall $$\mathbf{A}\in \mathcal{P}$$.      $$\blacksquare$$   Q.E.D.


