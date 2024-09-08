---
layout: page
title: Spectral representation of dissipation in spherical coordinates
description: Representation of the volumetric integral of squared curl of a vector field, in terms of the spectral coefficients of the vector field
importance: 1
date: 2024-09-08 12:00:00-0400
category: Computation
---



In some applications, we are interested in the quantity

$$
\mathscr{D} = \int_{B} |\nabla\times \mathbf{A}|^2\, dV
$$

where $$B$$ denotes a unit ball in 3-D space, $$\mathbf{A}$$ a solenoidal field, i.e. $$\nabla\cdot \mathbf{A} = 0$$. The condition that $$\mathbf{A}$$ is solenoidal perhaps seems a bit restrictive, but such fields naturally arise when $$\mathbf{A}$$ represents the velocity field of a incompressible, uniform density fluid, or a general magnetic field. This integral naturally arise when calculating e. g. the viscous dissipation in incompressible fluid,

$$
\mathcal{E}(\mathbf{u}) = \int_B |\nabla\times \mathbf{u}|^2\, dV = \int_B |\nabla \mathbf{u}|^2\, dV
$$

which is also called *enstrophy*, and when calculating Ohmic dissipation,

$$
\mathscr{D}_I = \int_B |\nabla\times \mathbf{B}|^2\, dV.
$$

Since the field is solenoidal, and is defined within a sphere, we have the toroidal-poloidal representation of such vector field $$\mathbf{A}$$,

$$
\mathbf{A} = \nabla\times T \mathbf{r} + \nabla\times \nabla\times S\mathbf{r}
$$

and the spectral representation of the toroidal and poloidal scalars

$$
\begin{aligned}
T(\mathbf{r}) &= \sum_{lmn} T_{lmn}\, R_n^{lm}(r) \,Y_l^m(\theta, \phi), \\
S(\mathbf{r}) &= \sum_{lmn} S_{lmn}\, R_n^{lm}(r) \,Y_l^m(\theta, \phi),
\end{aligned}
$$

where $$\sum_{lmn} = \sum_{l=0}^L \sum_{m=-l}^l \sum_{n=0}^N$$, $$R_n^{lm}(r)$$ is some radial basis function. A popular choice is a spherical-harmonic-order-independent one-sided Jacobi polynomial, known as the (Jones-)Worland polynomial, $$W_n^l(r) \propto r^l P_n^{(-\frac{1}{2}, l-\frac{1}{2})}(2r^2 - 1)$$ ([Livermore et al. 2007](https://doi.org/10.1016/j.jcp.2007.08.026)). What, then, would be the representation of $$\mathscr{D}$$ purely in the spectral domain?



Let us first rewrite the curl of $$\mathbf{A}$$ in Helmholtz representation, but with surface operators,

$$
\begin{aligned}
\nabla\times \mathbf{A} &= \nabla\times \nabla\times T \mathbf{r} + \nabla\times \nabla\times \nabla\times S \mathbf{r}\\
&= \nabla_s \left(\frac{1}{r} \frac{\partial}{\partial r}(rT)\right) - \hat{r} \nabla_s^2 \frac{T}{r} - \nabla\times \left(\frac{1}{r^2} \frac{\partial}{\partial r}\left(r^2\frac{\partial P}{\partial r}\right) + \frac{1}{r^2} \nabla_s^2 S\right) \mathbf{r}
\end{aligned}
$$

where $$\nabla_s$$ is the surface gradient operator, and we used the properties of toroidal and poloidal fields. This is the Helmholtz representation of field $$\nabla\times \mathbf{A}$$, where we decompose it into a surface gradient term (first term), a surface curl term (third term), and a radial component (second term) ([see the notes on vector representations on the surface of a sphere]({% link _notes/surface_repr.md %})). We then substitute the scalars with their respective spectral expansion, and

$$
\begin{aligned}
\nabla\times \mathbf{A} &= \sum_{lmn} \bigg[T_{lmn} \frac{1}{r} \frac{d(rR_n^{lm})}{d r} \nabla_s Y_l^m - T_{lmn} \frac{R_n^{lm}}{r} \hat{\mathbf{r}} \nabla_s^2 Y_l^m \\
&\qquad \,\,\, - S_{lmn} \nabla\times \left(\frac{1}{r^2} \frac{d}{d r}\left(r^2\frac{dR_n^{lm}}{d r}\right) + \frac{R_n^{lm}}{r^2} \nabla_s^2\right)Y_l^m \mathbf{r}\bigg] \\
&= \sum_{lmn} \bigg[T_{lmn} \frac{1}{r} \frac{d(rR_n^{lm})}{d r} \nabla_s Y_l^m + T_{lmn} \frac{l(l+1)}{r} R_n^{lm} Y_l^m \hat{\mathbf{r}} \\ 
&\qquad \,\,\, - S_{lmn} \left(\frac{1}{r^2} \frac{d}{d r}\left(r^2\frac{dR_n^{lm}}{d r}\right) - \frac{l(l+1)}{r^2} R_n^{lm}\right) \nabla \times Y_l^m \mathbf{r}\bigg] \\ 
&= \sum_{lmn} \bigg[T_{lmn} \frac{1}{r} \frac{d(rR_n^{lm})}{d r} \mathbf{B}_l^m + T_{lmn} \frac{l(l+1)}{r} R_n^{lm} \mathbf{P}_l^m \\ 
&\qquad \,\,\, + S_{lmn} \left(\frac{l(l+1)}{r^2} R_n^{lm} - \frac{1}{r^2} \frac{d}{d r}\left(r^2\frac{dR_n^{lm}}{d r}\right)\right) \mathbf{C}_l^m\bigg]
\end{aligned}.
$$

where $$\mathbf{P}_l^m$$, $$\mathbf{B}_l^m$$ and $$\mathbf{C}_l^m$$ are the vector spherical harmonics. Using the orthogonality of the vector spherical harmonics, we have 

$$
\begin{aligned}
\mathscr{D} &= \int_B |\nabla\times \mathbf{A}|^2\, dV \\ 
&= \sum_{lm} \sum_{nn'} T_{lmn'}^* T_{lmn} \langle \mathbf{B}_l^m, \mathbf{B}_l^m \rangle_S
\int_0^1 \left(\frac{1}{r} \frac{d(rR_{n'}^{lm})}{d r}\right) \left(\frac{1}{r} \frac{d(rR_n^{lm})}{d r}\right) r^2 dr \\ 
&+ \sum_{lm} \sum_{nn'} T_{lmn'}^* T_{lmn} \langle \mathbf{P}_l^m, \mathbf{P}_l^m \rangle_S
\int_0^1 \left(\frac{l(l+1)}{r} R_{n'}^{lm}\right) \left(\frac{l(l+1)}{r} R_n^{lm}\right) r^2 dr \\ 
&+ \sum_{lm} \sum_{nn'} S_{lmn'}^* S_{lmn} \langle \mathbf{C}_l^m, \mathbf{C}_l^m \rangle_S \\
&\quad \times
\int_0^1 \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_{n'}^{lm} \cdot  \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_n^{lm} r^2 dr \\
&= \sum_{lm} \sum_{nn'} T_{lmn'}^* T_{lmn} \left[ l(l+1)
\int_0^1 \frac{d(rR_{n'}^{lm})}{d r} \frac{d(rR_n^{lm})}{d r} dr + l^2(l+1)^2
\int_0^1 R_{n'}^{lm} R_n^{lm} dr\right] \\ 
&+ \sum_{lm} \sum_{nn'} S_{lmn'}^* S_{lmn} l(l+1) \\
&\quad \times
\int_0^1 \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_{n'}^{lm} \cdot  \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_n^{lm} r^2 dr.
\end{aligned}
$$

Therefore, defining matrices

$$
\begin{aligned}
(\mathbf{M}^{lm}_{\mathscr{D}T})_{n'n} &= l(l+1)
\int_0^1 \frac{d(rR_{n'}^{lm})}{d r} \frac{d(rR_n^{lm})}{d r} dr + l^2(l+1)^2
\int_0^1 R_{n'}^{lm} R_n^{lm} dr \\ 
(\mathbf{M}^{lm}_{\mathscr{D}S})_{n'n} &= l(l+1)
\int_0^1 \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_{n'}^{lm}  \left(\frac{l(l+1)}{r^2} - \frac{1}{r^2} \frac{d}{d r}r^2\frac{d}{d r}\right) R_n^{lm} r^2 dr \\ 
\end{aligned}
$$

the volume integral can be written in the quadratic form

$$
\mathscr{D} = \int_B |\nabla\times \mathbf{A}|^2\, dV = \sum_{lm} \left[\mathbf{T}_{lm}^H \mathbf{M}_{\mathscr{D}T}^{lm} \mathbf{T}_{lm} + \mathbf{S}_{lm}^H \mathbf{M}_{\mathscr{D}S}^{lm} \mathbf{S}_{lm}\right].
$$

This gives the representation of $$\mathscr{D}$$ purely in terms of spectral coefficients of $$\mathbf{A}$$. The specific form of the matrix depends on the radial basis of choice, but these matrices are usually dense (e.g. for Worland polynomials).




