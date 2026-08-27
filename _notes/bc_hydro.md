---
layout: page
title: Kinematic boundary conditions for fluid dynamics in spherical geometry
description: Representation of stress-free BC for anelastic/Boussinesq flows
importance: 1
date: 2026-08-26 12:00:00-0400
category: Physics
---

## Stress-free boundary condition

The stress tensor for Newtonian fluid is given by

$$
\sigma = \rho \nu \dot{\varepsilon}
$$

where $$\dot{\varepsilon}$$ is the strain rate tensor given by

$$
\dot{\varepsilon} = \nabla \mathbf{u} + \nabla \mathbf{u}^\top - \frac{2}{3}(\nabla\cdot\mathbf{u})\mathbf{I}.
$$

Stress-free boundary condition dictates that the tangential components of the surface traction vanishes, i.e.  $$\hat{\mathbf{n}}\times (\hat{\mathbf{n}} \cdot \sigma)\vert_{\partial V} = \mathbf{0}$$; equivalently, this means that the tangential components of the surface strain rate vanishes, i.e. $$\hat{\mathbf{n}}\times (\hat{\mathbf{n}} \cdot \dot{\varepsilon})\vert_{\partial V} = \mathbf{0}$$. Here $$\hat{\mathbf{n}}$$ is the surface normal and is equal to $$\hat{\mathbf{r}}$$ in spherical geometry. Therefore, the condition on the stress can be transferred to the strain rate, dictating that the tangential components of the *normal directional strain rate* ($$\hat{\mathbf{n}}\cdot \dot{\varepsilon}$$) vanishes on the surface. In terms of velocity, the normal directional strain rate takes the form

$$
\begin{aligned}
&\hat{\mathbf{n}}\cdot \dot{\varepsilon} = \hat{\mathbf{r}}\cdot \dot{\varepsilon} \\
&= \hat{\mathbf{r}} \cdot \left[\nabla \mathbf{u} + \nabla \mathbf{u}^\top - \frac{2}{3}(\nabla\cdot\mathbf{u})\mathbf{I} \right] \\
&= \partial_r \mathbf{u} + \nabla \mathbf{u} \cdot \hat{\mathbf{r}} - \frac{2}{3}(\nabla\cdot\mathbf{u})\hat{\mathbf{r}} \\
&= (\partial_r u_r \hat{\mathbf{r}} + \partial_r \mathbf{u}_H) + \nabla (\mathbf{u} \cdot \hat{\mathbf{r}}) - \nabla \hat{\mathbf{r}} \cdot \mathbf{u} - \frac{2}{3}(\nabla\cdot\mathbf{u})\hat{\mathbf{r}} \\
&= (\partial_r u_r \hat{\mathbf{r}} + \partial_r \mathbf{u}_H) + \nabla u_r - \frac{1}{r}(\mathbf{I} - \hat{\mathbf{r}}\hat{\mathbf{r}}) \cdot \mathbf{u} - \frac{2}{3}(\nabla\cdot\mathbf{u})\hat{\mathbf{r}} \\
&= (\partial_r u_r \hat{\mathbf{r}} + \partial_r \mathbf{u}_H) + \nabla u_r - \frac{\mathbf{u} - u_r \hat{\mathbf{r}}}{r} - \frac{2}{3}(\nabla\cdot\mathbf{u})\hat{\mathbf{r}} \\
&= \hat{\mathbf{r}} \left[2\partial_r u_r - \frac{2}{3}(\nabla\cdot\mathbf{u})\right] + \left[\partial_r \mathbf{u}_H + \nabla_H u_r - \frac{\mathbf{u}_H}{r}\right]
\end{aligned}
$$

where the radial / surface-normal component and the horizontal / surface-tangent components have been separated, and the subscript $$H$$ indicates horizontal component / differential. The radial part is unconstrained, where the surface-tangent components need to vanish at the surface, hence

$$
\left(\partial_r \mathbf{u}_H + \nabla_H u_r - \frac{\mathbf{u}_H}{r}\right)\bigg\vert_{\partial V} = \mathbf{0}
$$

Under no-penetration boundary condition (which is almost always the case in simulations in spherical geometry), we have $$(\nabla_H u_r)\vert_{\partial V} = \nabla_H u_r\vert_{\partial V} = \mathbf{0}$$. The kinematic condition therefore simplifies to

$$
\begin{aligned}
\left(\partial_r \mathbf{u}_H - \frac{\mathbf{u}_H}{r}\right)\bigg\vert_{\partial V} &= \mathbf{0}\\
\text{or}\quad\frac{\partial}{\partial r} \left(\frac{\mathbf{u}_H}{r}\right)\bigg\vert_{\partial V} &= \mathbf{0}.
\end{aligned}
$$

### Tor-Pol representation, incompressible

Under incompressible approximation, the solenoidal velocity field can be represented using one toroidal and one poloidal scalar, via

$$
\begin{aligned}
\mathbf{u} &= \nabla\times T\mathbf{r} + \nabla\times \nabla\times P \mathbf{r} \\
&= \nabla_s T \times \hat{\mathbf{r}} + \nabla_s \frac{1}{r}\partial_r(rP) - \hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} 
\end{aligned}
$$

where $$\nabla_s$$ is the angular gradient (the dimensionless form of the horizontal gradient $$\nabla_H$$, i.e. $$\nabla_s = r \nabla_H$$), and $$\nabla_s^2$$ is the angular Laplacian. Substituting the horizontal components in the stress-free boundary condition, 

$$
\partial_r \left(\frac{\mathbf{u}_H}{r}\right)\bigg\vert_{\partial V} = \nabla_s \partial_r\left(\frac{T}{r}\right)\bigg\vert_{\partial V} \times \hat{\mathbf{r}} + \nabla_s \partial_r\left[\frac{1}{r^2}\partial_r(rP)\right]\bigg\vert_{\partial V} = \mathbf{0}
$$

Considering that toroidal and poloidal components are linearly independent function spaces on the surface of the sphere, and the uniqueness of representing a surface-tangent vector field in toroidal and poloidal scalars (up to some constant) (this is equivalently the Helmholtz decomposition theorem on a surface), we can write

$$
\left\{\begin{aligned}
\frac{\partial}{\partial r}\left(\frac{T}{r}\right)\bigg\vert_{\partial V} = \frac{1}{r} \left(\frac{\partial T}{\partial r} - \frac{T}{r}\right)\bigg\vert_{\partial V} = 0 \\
\frac{\partial}{\partial r}\left[\frac{1}{r^2}\frac{\partial}{\partial r}(rP)\right]\bigg\vert_{\partial V} = \frac{1}{r} \left(\frac{\partial^2 P}{\partial r^2} - \frac{2P}{r^2}\right)\bigg\vert_{\partial V} = 0
\end{aligned}\right.
$$

Given that no-penetration condition requires $$P\vert_{\partial V} = 0$$, the poloidal condition is simply

$$
P\vert_{\partial V} = 0 \quad \& \quad \partial_r^2 P\vert_{\partial V} = 0.
$$

### Tor-Pol representation, anelastic

The boundary condition for toroidal poloidal scalars in the anelastic approximation is very similar, just a bit more complicated. In anelastic approximation, since $$\nabla\cdot (\bar{\rho} \mathbf{u}) = 0$$, the mass flux instead of the flow is solenoidal, and can be represented via the toroidal-poloidal decomposition

$$
\bar{\rho}\mathbf{u} = \nabla_s T \times \hat{\mathbf{r}} + \nabla_s \frac{1}{r}\partial_r(rP) - \hat{\mathbf{r}} \nabla_s^2 \frac{P}{r}
$$

Assuming that the background density profile $$\bar{\rho}$$ is simply a function of $$r$$, i.e. background has spherical symmetry, multiplication and division of $$\bar{\rho}$$ commute with all angular operators. The stress-free boundary condition yields

$$
\partial_r \left(\frac{\mathbf{u}_H}{r}\right)\bigg\vert_{\partial V} = \nabla_s \partial_r\left(\frac{T}{\bar{\rho}r}\right)\bigg\vert_{\partial V} \times \hat{\mathbf{r}} + \nabla_s \partial_r\left[\frac{1}{\bar{\rho}r^2}\partial_r(rP)\right]\bigg\vert_{\partial V} = \mathbf{0},
$$

which in turn yields the toroidal condition

$$
\frac{\partial}{\partial r}\left(\frac{T}{\bar{\rho}r}\right)\bigg\vert_{\partial V} = 0
$$

and the poloidal condition

$$
\begin{aligned}
\frac{\partial}{\partial r}\left[\frac{1}{\bar{\rho}r^2}\frac{\partial}{\partial r}(rP)\right]\bigg\vert_{\partial V} = 0 \\
\frac{\partial}{\partial r}\left[\frac{\partial_r P}{\bar{\rho}r} + \frac{P}{\bar{\rho}r^2} \right]\bigg\vert_{\partial V} = 0 \\
\left[\frac{\partial_r^2 P}{\bar{\rho}r} + \frac{\partial_r P}{r} \partial_r \frac{1}{\bar{\rho}} + P \partial_r \frac{1}{\bar{\rho} r^2}\right]_{\partial V} = 0
\end{aligned}
$$

Again, if under no-penetration condition, $$P\vert_{\partial V} = 0$$, then the poloidal condition for stress-free boundary reduces to

$$
\left[\frac{\partial_r^2 P}{\bar{\rho}r} + \frac{\partial_r P}{r} \partial_r \frac{1}{\bar{\rho}}\right]_{\partial V} = \frac{1}{r} \frac{\partial}{\partial r} \left(\frac{\partial_r P}{\bar{\rho}}\right)\bigg\vert_{\partial V} = 0
$$

We also see that condition re\verts back to $$\partial_r^2 P\vert_{\partial V} = 0$$ when $$\bar{\rho} = \text{Cst}.$$, which is the case under the incompressible approximation.

