---
layout: page
title: Adjoint method 1 - Adjoint of operators
description: First tool for adjoint method - what is an adjoint?
importance: 1
date: 2023-08-20 12:00:00-0400
category: Maths
---



Adjoint method is a powerful method for computing Fréchet derivatives of functionals involving solutions to differential equations. It is commonly used in inverse problems, data assimilations, optimal controls and fields concerning PDE-constrained optimization. Typically, a set of adjoint equations is developed in addition to the original forward equation; the derivative is computed based on the solutions to both the original and the adjoint system.

Although I have come across the adjoint method quite several times, first in seismology and full waveform inversion (FWI), then in electromagnetic induction sounding, and most recently in fluid dynamics and geodynamo problems, I feel that I never truly get the gist of it. A question that I often ask myself: if given an arbitrary set of PDEs, and an objective function involving the observables, will I be able to derive the adjoint equations and express the necessary Fréchet derivatives in terms of original and adjoint solutions? To this question, my answer has always been uncertain, inclined towards negative. I decide therefore that it is now time to develop some more systematic understanding of this method.

The challenge is that most of the texts on this topic are buried within *actual* mathematical literature. One cannot truly understand adjoint method unless one is apt with functional analysis. Unfortunately, I have no formal background in this level of mathematics. What I try to do here is try to collect a self-contained compilation of tools and theories required to develop the adjoint method.

## Adjoint of Operators

The reason why the adjoint method is called "adjoint" method is because the operators are moved to its adjoint in the process. In other words, the adjoint systems are just formed by the adjoint operators of the original operators.

The prerequisite for defining the adjoint is an original operator on a Hilbert space. Let $$L$$ be a linear operator on a Hilbert space $$\mathcal{H}$$, with inner product $$(f, g)$$. The adjoint operator $$L^*$$ is defined as the operator that fulfills the Lagrange's identity

$$
\langle f, Lg\rangle = \langle L^*f, g \rangle, \qquad \forall f, g \in \mathcal{H}
$$

If $$L^* = L$$, the operator is called *self-adjoint*.

### Finite-dimensional Hilbert space: Adjoint of matrices

The adjoints of operators are very straightforward in finite dimensions, where the Hilbert space is a finite-dimensional complex vector space $$\mathbb{C}^n$$, equipped with the inner product $$\langle u, v \rangle = u^\mathsf{H} v$$. The linear transforms on this vector space is simply a matrix $$L\in \mathbb{C}^{n\times n}$$, and

$$
\langle u, Lv\rangle = u^\mathsf{H} Lv=(L^\mathsf{H} u)^\mathsf{H} v = \langle L^\mathsf{H} u, v\rangle \quad \Longrightarrow \quad L^* = L^\mathsf{H}
$$

therefore the adjoint of a matrix is nothing but its conjugate transpose. When translated to the language of matrices, self-adjointness simply means *Hermitian* $$L^\mathsf{H} = L$$. It follows that adjoint can be considered as a generalization of conjugate transposition to operators on arbitrary, esp. infinite dimensional, vector spaces.

### General second-order differential operator

Consider a Hilbert space $$\mathcal{H}$$ of twice differentiable functions defined on a domain in $$\mathbb{R}^n$$, equipped with the the inner product

$$
\langle f, g \rangle = \int_\Omega \overline{f(\mathbf{r})} \, g(\mathbf{r})\, d\mathbf{r}
$$

The differential operator of second order operating on these functions takes the general form

$$
L = \sum_{i,j} a_{ij} \partial_i \partial_j + \sum_{i} b_i \partial_i + c = \mathbf{A}: \nabla\nabla + \mathbf{b}\cdot \nabla + c
$$

The inner product with this operator can be written as

$$
\begin{aligned}
\langle f,Lg \rangle &= \sum_{i,j} \langle f, a_{ij}\partial_i\partial_j g\rangle + \sum_i \langle f, b_i\partial_i g\rangle + c\langle f,g\rangle \\ 
&= \sum_{i,j} \int_\Omega \overline{f}\, a_{ij} \partial_i \partial_j g\, d\mathbf{r} + \sum_i \int_\Omega \overline{f} b_i \partial_i g\, d\mathbf{r} + c\int_\Omega \overline{f} g\, d\mathbf{r} \\ 
&= \int_\Omega \overline{f}\mathbf{A}: \nabla\nabla g\, d\mathbf{r} + \int_\Omega \overline{f} \, \mathbf{b}\cdot \nabla g\, d\mathbf{r} + c\int_\Omega \overline{f} g\, d\mathbf{r}
\end{aligned}
$$

Note that using vector identities (or basic calculus on component form),

$$
\begin{aligned}
\overline{f} a_{ij} \partial_i \partial_j g &= \partial_i \left(a_{ij}\overline{f} \partial_j g\right) - \partial_i(a_{ij} \overline{f}) \partial_j g \\
&= \partial_i \left(a_{ij}\overline{f} \partial_j g\right) - \partial_j \left( \partial_i(a_{ij} \overline{f}) g \right) + g \partial_j\partial_i \left(a_{ij} \overline{f}\right) \\ 
\overline{f} \mathbf{A}: \nabla\nabla g &= \nabla\cdot \left(\overline{f} \mathbf{A}\cdot \nabla g - g \nabla\cdot (\overline{f} \mathbf{A}) \right) + g \nabla\nabla : (\overline{f}\mathbf{A}) \\ 
\overline{f} b_i \partial_i g &= \partial_i \left(b_i \overline{f}g\right) - g \partial_i \left(\overline{f} b_i\right) \\ 
\overline{f}\mathbf{b}\cdot \nabla g &= \nabla\cdot \left(\overline{f} g \mathbf{b}\right) - g \nabla\cdot \left(\overline{f} \mathbf{b}\right)
\end{aligned}
$$

The linear operator on $$g$$ can be moved to $$f$$, although changed in form:

$$
\begin{aligned}
\langle f, Lg\rangle &= \int_\Omega g \nabla\nabla : \left(\overline{f} \mathbf{A}\right) \, d\mathbf{r} - \int_\Omega g \nabla\cdot \left(\overline{f} \mathbf{b}\right)\, d\mathbf{r} + c\int_\Omega \overline{f} g \, d\mathbf{r} \\ 
&+ \oint_{\partial \Omega} \left(\overline{f} \mathbf{A}\cdot \nabla g - g \nabla\cdot (\overline{f} \mathbf{A}) + g\overline{f}\mathbf{b}\right) \cdot d\mathbf{S} \\ 
&= \int_\Omega \overline{\left(\nabla\nabla : (\overline{\mathbf{A}}f) - \nabla\cdot (\overline{\mathbf{b}} f) + \overline{c} f\right)} \, g\, d\mathbf{r} \\ 
&+ \oint_{\partial \Omega} \left(\overline{f} \mathbf{A}\cdot \nabla g - g \nabla\cdot (\overline{f} \mathbf{A}) + g\overline{f}\mathbf{b}\right) \cdot d\mathbf{S} \\ 
\langle f, Lg\rangle &= \langle L^* f, g\rangle + \oint_{\partial \Omega} \mathbf{T}\cdot d\mathbf{S}
\end{aligned}
$$

Therefore the adjoint $$L^*$$ for the general second-order differential operator reads

$$
L^* = \sum_{i,j} \partial_i \partial_j \overline{a}_{ij}^M - \sum_{i} \partial_i \overline{b}_i^M + \overline{c} = \nabla\nabla:\overline{\mathbf{A}}^M - \nabla\cdot \overline{\mathbf{b}}^M + \overline{c}.
$$

Here the superscript $$M$$ denotes a multiplication operator, as used in Backus. The necessary boundary condition for the Hilbert space is

$$
\left(\overline{f} \mathbf{A}\cdot \nabla g - g \nabla\cdot (\overline{f} \mathbf{A}) + g\overline{f}\mathbf{b}\right)_{\partial \Omega} \cdot \hat{\mathbf{n}} = 0
$$

### Common linear differential operators

#### Laplacian
With the previous derivations, we can easily obtain the adjoint operators of common second-order differential operators. First, let us look at the ***Laplacian*** $$L = \nabla^2 = \mathbf{I}:\nabla\nabla$$. The adjoint operator takes the form

$$
L^* = \nabla \nabla:\mathbf{I}^M = \nabla^2 = L
$$

Therefore the operator is self-adjoint, under the boundary condition

$$
\left(\overline{f}\nabla g - g\nabla \overline{f}\right)\cdot \hat{\mathbf{n}} = \overline{f} \frac{\partial g}{\partial n} - g \frac{\partial \overline{f}}{\partial n} = 0.
$$

For the Laplacian operator, any homogeneous *Robin-type boundary condition* with real coefficients $$\alpha f + \beta \partial_n f = 0$$ for both $$f$$ and $$g$$ will satisfy the aforementioned condition.

#### Wave operator
The self-adjointness is not specific to Laplacian; it turns out any $$\mathbf{A} = Cst. \in \mathbb{R}^{n\times n}$$ (the two other coefficients set to zero) will yield self-adjoint operators, given the appropriate boundary conditions. For instance, the wave operator, or d'Alembert operator

$$
\square = \frac{1}{c^2} \frac{\partial^2}{\partial t^2} - \nabla^2
$$

where $$\nabla^2$$ is the Laplacian in the spatial dimensions, is a a second-order operator in the space-domain continuum. Introducing $$\nabla_{\mathbf{r},t} = \hat{\mathbf{t}}  \partial_t + \hat{\mathbf{r}}\nabla$$, we consider the operator as operating on a Hilbert space of functions defined on $$(t, x_{i=1:N}) \in \mathbb{R}^{N+1}$$

$$
\square = \frac{1}{c^2}\partial_t^2 - \partial_i \partial_i = \begin{pmatrix}1/c^2 & \mathbf{0} \\ \mathbf{0} & -\mathbf{I}_N\end{pmatrix} : \nabla_{\mathbf{r},t}\nabla_{\mathbf{r},t}
$$

Its adjoint is again, itself, making the wave operator self-adjoint,

$$
\square^* = \nabla_{\mathbf{r}, t} \nabla_{\mathbf{r}, t} : \begin{pmatrix}1/c^2 & \mathbf{0} \\ \mathbf{0} & -\mathbf{I}_N\end{pmatrix} = \frac{1}{c^2} \partial_t^2 - \nabla^2 = \square.
$$

The boundary condition to be satisified

$$
\overline{f} \hat{\mathbf{n}}\cdot \begin{pmatrix}1/c^2 & \mathbf{0} \\ \mathbf{0} & -\mathbf{I}_N \end{pmatrix} \cdot \nabla_{\mathbf{r}, t} g - g \nabla_{\mathbf{r},t}f \cdot \begin{pmatrix}1/c^2 & \mathbf{0} \\ \mathbf{0} & -\mathbf{I}_N\end{pmatrix} \cdot \hat{\mathbf{n}} = 0
$$

This comprises both boundary conditions in time and in space. Let us further assume that the problem is defined on $$[t_0, t_1] \times \Omega$$, with $$\Omega \in \mathbb{R}^n$$ is the spatial domain. At the temporal boundary $$\hat{\mathbf{n}} = \pm \hat{\mathbf{t}}$$, we have

$$
\left[\overline{f} \frac{\partial g}{\partial t} - g \frac{\partial \overline{f}}{\partial t}\right]_{t_0, t_1} = 0,\quad 
$$

and at the space boundary, the same boundary condition as for Laplacian applies

$$
\overline{f} \frac{\partial g}{\partial n} - g \frac{\partial \overline{f}}{\partial n} = 0.
$$

These two conditions correspond to the boundary conditions required in seismology to prove the theorem of source-receiver reciprocity, also called ***Betti's theorem of reciprocity*** i.e. reciprocal property of Green's function: the first can be satisfied with a "quiescent" past for the original wavefield $$g$$ and a quiescent "future" for the adjoint field $$f$$, and the second can be satisfied with either free-surface or no-slip boundary condition.
*Final remark*: the same operator can also be expressed using the Minkowski metric, in which case $$\square$$ is really just a Laplacian in Minkowski space.

#### Operators in Sturm-Liouville problems
The Sturm-Liouville problem is given by equation

$$
\frac{d}{dx} \left[p(x) \frac{dy}{dx}\right] + q(x) y = \lambda \, r(x)y,\qquad x\in(a,b)
$$

with some homogeneous boundary condition. The problem is a *generalized eigenvalue problem*, but can be easily converted to an ordinary eigenvalue problem given $$r(x)>0$$:

$$
Ly=\lambda y,\qquad L = \frac{1}{r(x)}\frac{d}{dx}\left[p(x)\frac{dy}{dx}\right] + \frac{q(x)}{r(x)}
$$

If we take $$p(x), q(x), r(x)$$ real continuous functions, and $$p(x)$$ has continuous derivative, and introduce the Hilbert space equipped with inner product

$$
\langle f, g\rangle = \int_a^b f(x)g(x)\, r(x)\,dx,
$$

then the adjoint can be developed:

$$
\begin{aligned}
\langle f, Lg\rangle &= \int_a^b f\left[\frac{1}{r}\frac{d}{dx}\left(p\frac{dg}{dx}\right) + \frac{q}{r}g \right]r\, dx \\ 
&= \int_a^b f\frac{d}{dx}\left(p\frac{dg}{dx}\right) \, dx + \int_a^b f q g \, dx \\ 
&= \int_a^b \frac{d}{dx}\left(p\frac{df}{dx}\right) g\,dx + \int_a^b fqg\, dx + \left[p\left(f\frac{dg}{dx} - g\frac{df}{dx}\right)\right]_a^b \\ 
&= \int_a^b \left[\frac{1}{r}\frac{d}{dx}\left(p\frac{df}{dx}\right) + \frac{q}{r}f \right]g \,r\, dx + \left[p\left(f\frac{dg}{dx} - g\frac{df}{dx}\right)\right]_a^b \\
&= \langle Lf, g\rangle + \left[p\left(f\frac{dg}{dx} - g\frac{df}{dx}\right)\right]_a^b
\end{aligned}
$$

Once again whenever some (Neumann/Dirichlet/Robin) homogeneous boundary condition is given, the boundary term will vanish. The linear differential operator associated with Sturm-Liouville problems is therefore self-adjoint.

#### Diffusion operator
Finally, we look at a non-self-adjoint operator. The diffusion operator is given by

$$
L = \frac{\partial}{\partial t} - \alpha \nabla^2
$$

where $$\alpha$$ is some diffusivity. As in wave operator, we can extend the $$N$$ spatial dimensions into $$N+1$$ dimensions, and write $$(t, x_i=1:N)$$ as the coordinate system. In this configuration, the operator corresponds to a second-order differential operator with

$$
\mathbf{A} = \begin{pmatrix} 0 & \\ &-\alpha \mathbf{I} \end{pmatrix},\quad \mathbf{b} = \begin{pmatrix}1 \\ \mathbf{0} \end{pmatrix}.
$$

Following the derived equation, the adjoint is given by

$$
L^* = - \frac{\partial}{\partial t} -\alpha \nabla^2 \neq L
$$

with temporal and spatial boundary conditions

$$
\left(\overline{f} g\right)_{t_0, t_1} = 0,\qquad \left(\overline{f} \frac{\partial g}{\partial n} - g \frac{\partial \overline{f}}{\partial n}\right)_{\partial \Omega} = 0.
$$

The diffusion operator is thus not self-adjoint.

