---
layout: page
title: Boundary conditions for magnetohydrodynamics
description: Electromagnetic and kinematic boundary conditions that is used in MHD.
importance: 1
date: 2023-06-15 12:30:00-0400
category: Physics
---

---

## Electromagnetic boundary conditions

### Insulating boundary for sphere

Setup: a electrically conductive sphere with finite conductivity, in contact with a perfect insulating exterior, which extends to infinity. There are no imposed or conducted currents anywhere outside the sphere. The electromagnetic boundary condition requires 
- continuity of boundary-normal magnetic field $$\hat{\mathbf{n}}\cdot[\mathbf{B}] = 0$$, absolutely required by solenoidal property of magnetic field
- continuity of boundary-tangent electric field $$\hat{\mathbf{n}}\times[\mathbf{E}] = \mathbf{0}$$, absolutely required by Faraday's law and magnetic field being finite
- continuity of boundary-tangent magnetic field $$\hat{\mathbf{n}}\times [\mathbf{B}] = \mathbf{0}$$, required by Ampere's law on condition that there is no current sheet (=infinitely large current density concentrated in infinitely thin sheet)
The last seems to have been argued on the ground that a current sheet would diffuse into the interior of the conductive fluid (see *Treatise*).

For the geodynamo problem, for some reason yet unbeknown to me, that the continuity of the electric field is not usually enforced or implemented. The boundary condition that is actually used is the continuity of the magnetic field

$$
[\mathbf{B}] = \mathbf{0}
$$

***Corollary***: when the tangent components of magnetic fields are continuous, by nature the curl of the magnetic field normal to the plane must be continuous. This can be easily verified by constructing closed rectangular loops whose enclosed surfaces are parallel to the boundary at each side of the boundary. Therefore,

$$
\hat{\mathbf{n}}\cdot [\nabla\times \mathbf{B}] = 0
$$

On the other hand, for the insulating exterior, if displacement current is neglected (*this is another assumption, which arises when the frequency is low enough. For the conductive medium, it means $$\omega \varepsilon \ll \sigma$$; for the insulator, it means the $$c/\omega$$ is much greater than the length scale on which the field varies. This pre-Maxwell form is used everywhere in core dynamics and EM sounding communities, but becomes a bit problematic when one wants to deal with energy flux in idealized insulating medium*), then $$\nabla\times \mathbf{B}=0$$ everywhere in the insulating region. To pair with this, one must have

$$
\hat{\mathbf{n}}\cdot (\nabla\times \mathbf{B}) = 0
$$

at the boundary.
The same condition can also be derived from the continuity of normal electric currents

$$
\hat{\mathbf{n}}\cdot [\mathbf{j}] = 0
$$

since there is no current in the insulating medium, it follows that

$$
\hat{\mathbf{n}}\cdot \mathbf{j} = \hat{\mathbf{n}}\cdot (\frac{1}{\mu_0}\nabla\times \mathbf{B}) = 0
$$

for the conductive interior at the boundary.
Finally, I comment on the fact that mathematically, the conditions

$$
\hat{\mathbf{n}}\times [\mathbf{B}]=\mathbf{0},\quad \hat{\mathbf{n}}\cdot [\nabla\times \mathbf{B}]=0
$$

give in total three scalar conditions, of which each and only two of them are linearly independent. Therefore, one can either impose continuity of two tangent components, or impose the continuity of normal curl, complemented by continuity of one of tangent components. The two approaches are mathametically equivalent.

In general, one would have to solve for the fields in both domains by imposing the continuities as connection conditions. In this case, however, one can formulate the boundary conditions purely in terms of the field parameters within the sphere. Andy seems to call this technique "lumped" boundary condition, although I cannot find this term elsewhere.
The procedure is as follows. First, recall that the magnetic field is solenoidal, and so always have the Mie representation

$$
\mathbf{B} = \nabla \times (T \mathbf{r}) + \nabla\times \nabla\times (P \mathbf{r})
$$

and recall the following conclusions from vector identities

$$
\nabla\times (T \mathbf{r}) = \nabla T \times \mathbf{r} = \nabla_s T \times \hat{\mathbf{r}} 
$$

$$
\nabla\times \nabla\times (P\mathbf{r}) = -\mathbf{r}\nabla^2 P + \nabla\left(\frac{\partial}{\partial_r} (rP)\right) = -\hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} +\nabla_s \left(\frac{1}{r}\frac{\partial}{\partial r}(rP)\right)
$$
where $$\nabla_s$$ is the surface gradient, and $$\nabla_s^2$$ is the surface Laplacian.
The magnetic field in the conductive medium can then be written as

$$
\mathbf{B} = -\hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} + \nabla_s \left(\frac{1}{r}\frac{\partial}{\partial r}(rP)\right) + \nabla_s T \times \hat{\mathbf{r}}.
$$

If expanding the scalars in terms of spherical harmonics

$$
P = \sum_{l,m} p_l^m(r) Y_l^m(\theta,\phi),\qquad T=\sum_{l,m} t_l^m(r) Y_{l}^m(\theta,\phi)
$$

and recalling the spherical harmonics are eigenfunctions of surface Laplacian, we can write

$$
\mathbf{B} = \hat{\mathbf{r}} \sum_{l,m} \frac{l(l+1)}{r}p_l^m Y_l^m + \sum_{l,m} \frac{1}{r}\frac{d(rp_l^m)}{dr} \nabla_s Y_l^m + \sum_{l,m} t_l^m \nabla_sY_l^m\times \hat{\mathbf{r}}
$$

In the insulating region outside the sphere, the magnetic field is not only solenoidal, but also irrotational (because absence of currents). The solution can be simply described by a potential field, which, for the whole space outside the sphere, takes the form

$$
\mathbf{B}= -\nabla V = \hat{\mathbf{r}}\sum_{l,m} \frac{l+1}{r^{n+2}} \iota_l^m Y_l^m - \sum_{l,m}\frac{1}{r^{n+2}}\iota_l^m \nabla_s Y_l^m.
$$

There are several ways to proceed from here. One can write out the explicit form of the surface gradient $$\nabla_s = \hat{\mathbf{\theta}} \frac{\partial}{\partial\theta} + \hat{\mathbf{\phi}}\frac{1}{\sin\theta}\frac{\partial}{\partial \phi}$$, and equate all three components of the fields at the boundary. Here I simply make use of the fact that

$$
\mathbf{P}_l^m = Y_l^m \hat{\mathbf{r}},\quad \mathbf{B}_l^m=\nabla_s Y_l^m,\quad \mathbf{C}_l^m = \nabla_s Y_l^m \times \hat{\mathbf{r}}
$$

are three orthogonal vector basis **on** the surface of the sphere. Therefore, for the field to be continuous, the sufficient and necessary condition is

$$
\begin{aligned}
\frac{l(l+1)}{r_0} p_l^m &= \frac{l+1}{r_0^{n+2}} \iota_l^m \\ 
\frac{1}{r_0}\frac{d(rp_l^m)}{dr} &= - \frac{1}{r_0^{n+2}}\iota_l^m \\ 
t_l^m &= 0
\end{aligned}
$$

Cancelling out the exterior field coefficient from the first two equations, we have

$$
\begin{aligned}
\frac{d}{dr}(rp_l^m) + l p_l^m = \frac{d p_l^m}{dr} + (l+1)p_l^m &= 0\\
t_l^m &= 0
\end{aligned}
$$

which gives the boundary solely in terms of the field coefficients in the interior region. It can be easily shown that for any field that satisfies this condition, there is a field within the insulating medium exterior to the sphere so that the original boundary conditions are satisfied. Therefore, this set of BC is sufficient and necessary.


