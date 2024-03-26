---
layout: page
title: Parity of spherical harmonics
description: z-parity of spherical harmonics and poloidal toroidal fields expressed in spherical harmonics
importance: 1
date: 2024-03-24 12:00:00-0400
category: Maths
---


In this note I investigate the parity of a spherical harmonic mode with respect to the equatorial plane ($$z=0$$). The parity arises in the context of solving eigenvalue problems in a sphere. When solutions of different parities decouple, the system can be reduced to a smaller size, thus reducing the computation cost.

---
## Scalars in spherical harmonic expansion

Define **reversion of the $$z$$-component** of a vector field

$$
\mathcal{R}: \begin{pmatrix} a_x \\ a_y \\ a_z \end{pmatrix} \mapsto 
\begin{pmatrix} a_x \\ a_y \\ -a_z \end{pmatrix}
$$

When this operator is applied to the position vector, it equivalently constructs the inversion with respect to the equatorial plane, as

$$
\mathcal{R}\begin{pmatrix} x \\ y \\ z\end{pmatrix} = \begin{pmatrix} x\\ y \\ -z \end{pmatrix}
$$

such that it is equivalent to the following transform in coordinates:

$$
\mathcal{R}: \quad z \mapsto -z,\qquad \theta \mapsto \pi - \theta
$$

Define $$\mathcal{S}$$ as the space of scalar fields that are symmetric (even) w.r.t. the equatorial plane, i.e.

$$
f(\mathbf{r}) = f(\mathcal{R}\mathbf{r}),\quad \forall F \in \mathcal{S}
$$

and $$\mathcal{A}$$ as the space of scalar fields that are anti-symmetric (odd) w.r.t. the equatorial plane,

$$
f(\mathbf{r}) = -f(\mathcal{R}\mathbf{r}),\quad \forall F \in \mathcal{A}
$$

First of all, we note the following **property**:

$$
\begin{aligned}
f(\mathbf{r}) \, g(\mathbf{r}) &\in \mathcal{A}, \quad \forall f \in \mathcal{A}, g \in \mathcal{S} \\ 
f(\mathbf{r}) \, g(\mathbf{r}) &\in \mathcal{S}, \quad \forall f, g \in \mathcal{A} \\ 
f(\mathbf{r}) \, g(\mathbf{r}) &\in \mathcal{S}, \quad \forall f, g \in \mathcal{S}
\end{aligned}
$$

This just inherits from the property of even and odd functions. Even factors keep the parity of the original field, while odd factors flip the parity of the original field. A purely radially varying scalar field is always an even field. Therefore, a natural consequence is **that any radially varying factors do NOT affect the parity of the scalar field**. Now we consider the spherical harmonic expansion of a scalar field

$$
f(\mathbf{r}) = \sum_{l,m} f_l^m(\mathbf{r}) =\sum_{l,m} f_l^m(r) \, Y_l^m(\theta, \phi)
$$

Since the radially varying SH coefficients do not affect the parity of the overall field, the parity of the SH components can be simplified to studying the parity of the SH basis function itself. Note that $$Y_l^m(\theta, \phi) = P_l^m(\cos\theta) e^{im\phi}$$; therefore, the parity of spherical harmonics directly inherits from the even/odd property of the associated Legendre function. Using

$$
P_l^m(-x) = (-1)^{l-m} P_l^m(x)
$$

we have the parity of the spherical harmonics:

$$
Y_l^m(-\theta,\phi) = (-1)^{l-m} Y_l^m(\theta, \phi)
$$

This translates to the following symmetry:
- $$Y_l^m \in \mathcal{S}$$ / even / symmetric w.r.t. the equatorial plane, when $$l-m$$ is even, or $$l\equiv m \,(\mathrm{mod} 2)$$;
- $$Y_l^m \in \mathcal{A}$$ / odd / anti-symm w.r.t. the equatorial plane, when $$l-m$$ is odd, or $$l\equiv m + 1 \, (\mathrm{mod} 2)$$.

---
## Vectors fields described by spherical harmonics

For a vector field, the notion of symmetry with respect to the equatorial plane requires an additional reversion of the field itself. The space $$\mathcal{S}_1$$ will be used for denoting a space of vector fields who has mirror symmetry w.r.t. the equatorial plane, or

$$
\mathbf{F}(\mathbf{r}) = \mathcal{R} \mathbf{F}(\mathcal{R}\mathbf{r}),\quad \forall \mathbf{F} \in \mathcal{S}_1
$$

while $$\mathcal{A}_1$$ denotes a space of vector fields which is mirror anti-symmetric w.r.t. the equatorial plane,

$$
\mathbf{F}(\mathbf{r}) = -\mathcal{R} \mathbf{F}(\mathcal{R}\mathbf{r}),\quad \forall \mathbf{F} \in \mathcal{A}_1
$$

The symmetric / even class $$\mathcal{S}_1$$ is referred to as "quadrupole-like" (*QP*) in Jiawen's papers, and the anti-symmetric / odd class $$\mathcal{A}_1$$ is referred to as "dipole-like" (*DP*) in Jiawen's papers. To be more explicit, writing it in component form

$$
\begin{gathered}
\mathbf{F} \in \mathcal{S}_1 \quad \Longleftrightarrow \quad F_e \in \mathcal{S},\quad F_z \in \mathcal{A} \\ 
\mathbf{F} \in \mathcal{A}_1 \quad \Longleftrightarrow \quad F_e \in \mathcal{A},\quad F_z \in \mathcal{S}
\end{gathered}
$$

where $$F_e$$ denotes any equatorial component of the field.

### Toroidal vector fields

Consider a toroidal vector field $$\mathbf{F} \in \mathcal{T}$$, and hence

$$
\mathbf{F} = \nabla\times (T \mathbf{r}) = -\hat{r}\times \nabla_s T = -\frac{\partial T}{\partial \theta} \hat{\phi} + \frac{1}{\sin\theta}\frac{\partial T}{\partial \phi} \hat{\theta} = \frac{z}{s} \frac{\partial T}{\partial \phi} \hat{s} - \frac{\partial T}{\partial \theta} \hat{\phi} - \frac{\partial T}{\partial \phi} \hat{z}
$$

For the toroidal field, the surface curl $$\hat{\mathbf{r}}\times \nabla_s$$ commutes with any function of $$r$$ (see e.g. [[Vector Representation]]); hence, each spherical harmonic can be written as the radially varying factor multiplied by the surface curl operated on the spherical harmonics, which is really just the vector spherical harmonics. Here however I explicitly write out the component

$$
\mathbf{F}_l^m = t_l^m(r) \left[\left(im\frac{z}{s} Y_l^m\, \hat{s} - \frac{\partial Y_l^m}{\partial \theta} \hat{\phi}\right) - im Y_l^m\, \hat{z}\right]
$$

In the first bracket I grouped the horizontal components, and the vertical component is put aside. The question now boils down to determining the parity of the components. To be more precise, we only care about the symmetry properties of $$zY_l^m/s$$, $$\partial_\theta Y_l^m$$ and $$Y_l^m$$. For the last one, we have

$$
Y_l^m \in \left\{\begin{aligned}
\mathcal{S},\quad l-m\equiv 0\,(\mathrm{mod} 2) \\ 
\mathcal{A},\quad l-m\equiv 1\,(\mathrm{mod} 2)
\end{aligned}\right.
$$

This variable corresponds to the vertical component. The second term inherits its parity from the odd/even property of $$\partial_\theta P_l^m(\cos\theta)$$, which ultimately can be derived from symmetry of $$P_l^m(\cos\theta)$$:

$$
\frac{\partial Y_l^m}{\partial\theta} \in \left\{\begin{aligned}
\mathcal{A},\quad l-m\equiv 0\,(\mathrm{mod} 2) \\ 
\mathcal{S},\quad l-m\equiv 1\,(\mathrm{mod} 2)
\end{aligned}\right.
$$

And finally, combining the parity of $$Y_l^m$$, and the odd parity of the factor $$z$$, we have

$$
\frac{z}{s} Y_l^m \in \left\{\begin{aligned}
\mathcal{A},\quad l-m\equiv 0\,(\mathrm{mod} 2) \\ 
\mathcal{S},\quad l-m\equiv 1\,(\mathrm{mod} 2)
\end{aligned}\right.
$$

Combining all three relations together, we have the following parity of the spherical harmonic components of the toroidal field:

$$
\begin{aligned}
l-m\equiv 0 \, (\mathrm{mod}\, 2) \quad &\Longleftrightarrow \quad F_{le}^m \in \mathcal{A},\, F_{lz}^m \in \mathcal{S}, \quad \Longleftrightarrow\quad \mathbf{F}_l^m \in \mathcal{A}_1 \\ 
l-m\equiv 1 \, (\mathrm{mod}\, 2) \quad &\Longleftrightarrow \quad F_{le}^m \in \mathcal{S},\, F_{lz}^m \in \mathcal{A}, \quad \Longleftrightarrow \quad \mathbf{F}_l^m \in \mathcal{S}_1
\end{aligned}
$$

### Poloidal vector field

Consider a poloidal vector field $$\mathbf{F} \in \mathcal{P}$$, and hence

$$
\begin{aligned}
\mathbf{F} &= \nabla\times \nabla\times (P\mathbf{r}) = \nabla_s\left(\frac{1}{r}\frac{\partial (rP)}{\partial r}\right) - \hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} \\ 
&= \frac{1}{r}\frac{\partial^2 (rP)}{\partial r\partial\theta} \hat{\theta} + \frac{1}{r\sin\theta} \frac{\partial^2 (rP)}{\partial r \partial \phi} \hat{\phi} - \hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} \\ 
&= \left[\frac{1}{r}\frac{\partial^2 (rP)}{\partial r\partial\theta} \cos\theta -\sin\theta \nabla_s^2 \frac{P}{r}\right] \hat{\mathbf{s}} + \frac{1}{r\sin\theta} \frac{\partial^2 (rP)}{\partial r \partial \phi} \hat{\phi} \\
&\quad + \left[-\frac{1}{r}\frac{\partial^2 (rP)}{\partial r\partial\theta} \sin\theta  -\cos\theta \nabla_s^2 \frac{P}{r} \right] \hat{\mathbf{z}} \\
&= \left[\frac{z}{r^2}\frac{\partial^2 (rP)}{\partial r\partial\theta} - \frac{s}{r^2} \nabla_s^2 P \right] \hat{\mathbf{s}} + \frac{1}{s} \frac{\partial^2 (rP)}{\partial r \partial \phi} \hat{\phi} \\
&\quad + \left[-\frac{s}{r^2}\frac{\partial^2 (rP)}{\partial r\partial\theta} -\frac{z}{r^2} \nabla_s^2 P \right] \hat{\mathbf{z}}
\end{aligned}
$$

Expanding the scalar $$P = \sum_{l,m} p_l^m(r) Y_l^m(\theta, \phi)$$, we can isolate each spherical harmonic component

$$
\begin{aligned}
\mathbf{F}_l^m &= \left[\frac{d(rp_l^m)}{dr} \frac{z}{r^2} \frac{\partial Y_l^m}{\partial \theta} + l(l+1) \frac{s}{r^2} p_l^m Y_l^m \right] \hat{\mathbf{s}} + \frac{im}{s}\frac{d(rp_l^m)}{dr} Y_l^m \hat{\phi} \\
&+ \left[-\frac{d(rp_l^m)}{dr} \frac{s}{r^2} \frac{\partial Y_l^m}{\partial \theta} + l(l+1) \frac{z}{r^2} p_l^m Y_l^m\right] \hat{\mathbf{z}}
\end{aligned}
$$

The question now boils down to determining the parity of the components. In this case, we only care about the symmetry properties of $$Y_l^m$$, $$zY_l^m$$, $$\partial_\theta Y_l^m$$ and $$z\partial_\theta Y_l^m$$. The parity of the first three quantities are already given in previous discussions. The only new thing here is the last one. Combining the parity of $$\partial_\theta Y_l^m$$, and the odd parity of the factor $$z$$, we have

$$
z \frac{\partial Y_l^m}{\partial\theta} \in \left\{\begin{aligned}
\mathcal{S},\quad l-m\equiv 0\,(\mathrm{mod} 2) \\ 
\mathcal{A},\quad l-m\equiv 1\,(\mathrm{mod} 2)
\end{aligned}\right.
$$

Combining all relations together, we have the following parity of the spherical harmonic components of the poloidal field:

$$
\begin{aligned}
l-m\equiv 0 \, (\mathrm{mod}\, 2) \quad &\Longleftrightarrow \quad F_{le}^m \in \mathcal{S},\, F_{lz}^m \in \mathcal{A}, \quad \Longleftrightarrow\quad \mathbf{F}_l^m \in \mathcal{S}_1 \\ 
l-m\equiv 1 \, (\mathrm{mod}\, 2) \quad &\Longleftrightarrow \quad F_{le}^m \in \mathcal{A},\, F_{lz}^m \in \mathcal{S}, \quad \Longleftrightarrow \quad \mathbf{F}_l^m \in \mathcal{A}_1
\end{aligned}
$$


