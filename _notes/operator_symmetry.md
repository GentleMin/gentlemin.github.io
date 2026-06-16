---
layout: page
title: Reflection symmetry of operations in 3D
description: How does a field with reflectional symmetry change when it undergoes algebraic / differential operations?
importance: 1
date: 2026-06-15 12:00:00-0400
category: Maths
--- 


Suppose a field defined in the 3D Euclidean space has reflectional symmetry with respect to a plane. How does the symmetry change if it undergoes algebraic / differential operations? This note collects practical conclusions for use in this context.

<br />

---

## Definitions

I start by introduce some definitions of reflection symmetry of the fields. Apart from one or two notations, this part is essentially the same to that listed in [Parity of spherical harmonics](https://gentlemin.github.io/notes/parity_SH/).

Given transformation

$$
\mathcal{R}: \begin{pmatrix} a_x \\ a_y \\ a_z \end{pmatrix} \mapsto 
\begin{pmatrix} a_x \\ a_y \\ -a_z \end{pmatrix}
$$

we can define $$\mathcal{S}$$ (and $$A$$) as the spaces of scalar fields that are symmetric (anti-symmetric) w.r.t. the $$z=0$$ plane, i.e.

$$
\begin{aligned}
\mathcal{S} &= \{f:\ f(\mathbf{r}) = f(\mathcal{R}\mathbf{r})\quad \forall \mathbf{r}\in \mathbb{R}^3\}, \\
\mathcal{A} &= \{f:\ f(\mathbf{r}) = -f(\mathcal{R}\mathbf{r})\quad \forall \mathbf{r}\in \mathbb{R}^3\}
\end{aligned}
$$

where $$f: \mathbb{R}^3\mapsto \mathbb{R}$$ is a scalar function defined on 3D Euclidean space.

Similarly, let us define $$\mathcal{S}_1$$ (and $$A_1$$) as the spaces of vector fields ($$1$$-subscript for rank-$$1$$ tensors) that are symmetric (anti-symmetric) w.r.t. the $$z=0$$ plane, i.e.

$$
\begin{aligned}
\mathcal{S}_1 &= \{\mathbf{f}:\ \mathbf{f}(\mathbf{r}) = \mathcal{R} \mathbf{f}(\mathcal{R}\mathbf{r}) \quad \forall \mathbf{r}\in \mathbb{R}^3 \}, \\
\mathcal{A}_1 &= \{\mathbf{f}:\ \mathbf{f}(\mathbf{r}) = -\mathcal{R} \mathbf{f}(\mathcal{R}\mathbf{r})\quad \forall \mathbf{r}\in \mathbb{R}^3\}
\end{aligned}
$$

where $$\mathbf{f}: \mathbb{R}^3\mapsto \mathbb{R}^3$$ is a vector function defined on 3D Euclidean space. A spatially uniform field perpendicular to the plane of symmetry, $$\hat{\mathbf{z}}$$, for instance, is a anti-symmetric vector field.

For convenience (which will become obvious later), let us introduce an index for reflectional symmetry, $$\mu$$, which outputs $$1$$ for symmetric fields, and $$-1$$ for antisymmetric fields. In other words,

$$
\mu(\mathbf{f}) = \left\{\begin{aligned}
	& +1, \quad \mathbf{f} \in \mathcal{S}_r \\
	& -1, \quad \mathbf{f} \in \mathcal{A}_r
\end{aligned}\right.
$$

regardless of the rank of the tensor $$r$$ (if $$r=0$$, these are the scalar symmetry sets $$\mathcal{S}$$ and $$\mathcal{A}$$; if $$r=1$$, these are the vector symmetry sets $$\mathcal{S}_1$$, $$\mathcal{A}_1$$).

As a remark, these sets are linear spaces as they are defined by linear operations, hence they are close to addition and scalar products, i.e. if $$\mu(f) = \mu(g)$$ and $$a \in \mathbb{R}$$, 

$$
\mu(f + g) = \mu(f), \quad \mu(af) = \mu(f).
$$

where $$f$$ and $$g$$ in the equation above can be either scalar or vector fields.


<br />

---

## Properties

Here I list the symmetry transformation under some algebraic and differential operations.

<br />


### Scalar product

Product of two symmetric (or anti-symmetric) scalar fields is symmetric; product of one symmetric and one anti-symmetric scalar fields is anti-symmetric. In summary,

$$
\mu(fg) = \mu(f) \, \mu(g)
$$

***Proof***: Under the premise that $$\mu$$ is defined for $$f$$ and $$g$$ (i.e. $$f,g$$ are either symmetric or anti-symmetric), 

$$
f(\mathcal{R}\mathbf{r}) = \mu(f) \, f(\mathbf{r}), \quad
g(\mathcal{R}\mathbf{r}) = \mu(g) \, g(\mathbf{r}).
$$

Then their product $$w(\mathbf{r}) = f(\mathbf{r}) g(\mathbf{r})$$ satisfies

$$
\begin{aligned}
w(\mathcal{R}\mathbf{r}) &= f(\mathcal{R}\mathbf{r})\, g(\mathcal{R}\mathbf{r}) = [\mu(f) f(\mathbf{r})][\mu(g) g(\mathbf{r})] \\
&= [\mu(f)\mu(g)][f(\mathbf{r})g(\mathbf{r})] = [\mu(f)\mu(g)] \, w(\mathbf{r})
\end{aligned}
$$

Therefore

$$
\mu(w) = \mu(fg) = \mu(f) \, \mu(g). \qquad \square
$$

<br />

### Scalar product with vector

Product of two symmetric (or anti-symmetric) scalar & vector fields is symmetric; product of one symmetric and one anti-symmetric scalar / vector fields is anti-symmetric. In summary,

$$
\mu(f\mathbf{g}) = \mu(f) \, \mu(\mathbf{g})
$$

***Proof***: One can either prove this by showing the symmetry component by component, or show that the product $$\mathbf{w} = f\mathbf{g}$$ satisfies

$$
\begin{aligned}
\mathbf{w}(\mathcal{R}\mathbf{r}) &= f(\mathcal{R}\mathbf{r})\, \mathbf{g} (\mathcal{R}\mathbf{r}) \\
&= [\mu(f) f][\mu(g) \mathcal{R} \mathbf{g}(\mathbf{r})] \\
&= [\mu(f)\mu(g)][\mathcal{R}f(\mathbf{r})g(\mathbf{r})] \\
&= [\mu(f)\mu(g)] \, \mathcal{R} \mathbf{w}(\mathbf{r}). \qquad \square
\end{aligned}
$$

<br />

### Vector inner product

Inner product of two symmetric (or anti-symmetric) vector fields is symmetric; inner product of one symmetric and one anti-symmetric vector fields is anti-symmetric. In summary,

$$
\mu(\mathbf{f}\cdot \mathbf{g}) = \mu(\mathbf{f})\, \mu(\mathbf{g})
$$

***Proof***: Under the premise that $$\mu$$ is defined for $$\mathbf{f}$$ and $$\mathbf{g}$$, we have

$$
\mathbf{f}(\mathcal{R}\mathbf{r}) = \mu(\mathbf{f}) \, \mathcal{R}\mathbf{f}(\mathbf{r}), \quad
\mathbf{g}(\mathcal{R}\mathbf{r}) = \mu(\mathbf{g}) \, \mathcal{R}\mathbf{g}(\mathbf{r}).
$$

Note here we used the definition and the property $$\mathcal{R}^2 = \mathcal{I}$$, with $$\mathcal{I}$$ being identity, or $$\mathcal{R}=\mathcal{R}^{-1}$$. The inner product $$w(\mathbf{r}) = \mathbf{f}(\mathbf{r}) \cdot \mathbf{g}(\mathbf{r})$$ satisfies

$$
\begin{aligned}
w(\mathcal{R}\mathbf{r}) &= \mathbf{f}(\mathcal{R}\mathbf{r})\cdot \mathbf{g}(\mathcal{R}\mathbf{r}) \\
&= [\mu(\mathbf{f}) \mathcal{R}\mathbf{f}(\mathbf{r})]\cdot [\mu(\mathbf{g}) \mathcal{R}\mathbf{g}(\mathbf{r})] \\
&= \mu(\mathbf{f})\mu(\mathbf{g}) \mathcal{R}^2 \, [\mathbf{f}(\mathbf{r})\cdot \mathbf{g}(\mathbf{r})] \\
&= \mu(\mathbf{f})\mu(\mathbf{g}) \, w(\mathbf{r}).\quad \square
\end{aligned}
$$

<br />

### Vector cross product

Cross product of two symmetric (or anti-symmetric) vector fields is anti-symmetric; inner product of one symmetric and one anti-symmetric vector fields is symmetric. In summary,

$$
\mu(\mathbf{f}\times \mathbf{g}) = - \mu(\mathbf{f}) \, \mu(\mathbf{g})
$$

***Proof***: Under the premise that $$\mu$$ is defined for $$\mathbf{f}$$ and $$\mathbf{g}$$, we have

$$
\mathbf{f}(\mathcal{R}\mathbf{r}) = \mu(\mathbf{f}) \, \mathcal{R}\mathbf{f}(\mathbf{r}), \quad
\mathbf{g}(\mathcal{R}\mathbf{r}) = \mu(\mathbf{g}) \, \mathcal{R}\mathbf{g}(\mathbf{r}).
$$

The cross product $$\mathbf{w}(\mathbf{r}) = \mathbf{f}(\mathbf{r}) \times \mathbf{g}(\mathbf{r})$$ satisfies

$$
\begin{aligned}
w_i(\mathcal{R}\mathbf{r}) &= \sum_{j,k} \epsilon_{ijk} \, f_j(\mathcal{R}\mathbf{r}) \, g_k (\mathcal{R}\mathbf{r}) \\
&= \sum_{j,k} \epsilon_{ijk} \, [\mu(\mathbf{f}) \mathcal{R}_j f_j] [\mu(\mathbf{g}) \mathcal{R}_k g_k] \\
&= [\mu(\mathbf{f}) \mu(\mathbf{g})] \, \sum_{j,k} \epsilon_{ijk} \,  [ \mathcal{R}_j f_j \mathcal{R}_k g_k]
\end{aligned}
$$

Here we note that $$\mathcal{R}_1 \mathcal{R}_2 = 1 = - \mathcal{R}_3$$, $$\mathcal{R}_2 \mathcal{R}_3 = \mathcal{R}_1 \mathcal{R}_3 = -1 = - \mathcal{R}_1 = - \mathcal{R}_2$$. This allows the latter part of the equation to be written in a simple form:

$$
\sum_{j,k} \epsilon_{ijk} \mathcal{R}_j f_j \mathcal{R}_k g_k = - \mathcal{R}_i \sum_{j,k} \epsilon_{ijk} f_j g_k
$$

and hence 

$$
\begin{aligned}
w_i(\mathcal{R} \mathbf{r}) &= - [\mu(\mathbf{f}) \mu(\mathbf{g})] \mathcal{R}_i \, [\mathbf{f}\times\mathbf{g}]_i = [- \mu(\mathbf{f}) \mu(\mathbf{g})] [\mathcal{R} \mathbf{w}]_i \\
\mathbf{w}(\mathcal{R} \mathbf{r}) &= [- \mu(\mathbf{f}) \mu(\mathbf{g})] \, \mathcal{R} \mathbf{w}(\mathbf{r}). \quad \square
\end{aligned}
$$

<br />

### Scalar gradient

Gradient of a(n) symmetric (resp. anti-symmetric) scalar field produces a(n) symmetric (resp. anti-symmetric) vector field. In summary,

$$
\mu(\nabla f) = \mu(f)
$$

***Proof***: The gradient satisfies

$$
\begin{aligned}
(\nabla f)(\mathcal{R}\mathbf{r}) &= [\nabla (f(\mathbf{r}'))]_{\mathbf{r}'=\mathcal{R}\mathbf{r}} \\
&= [\nabla (\mu(f)f(\mathcal{R}\mathbf{r}'))]_{\mathbf{r}'=\mathcal{R}\mathbf{r}} \\
&= \mu(f) \, [\nabla (f(\mathcal{R}\mathbf{r}'))]_{\mathbf{r}'=\mathcal{R}\mathbf{r}} \\
&= \mu(f) \, \mathcal{R} [(\nabla f)(\mathcal{R}\mathbf{r}')]_{\mathbf{r}'=\mathcal{R}\mathbf{r}} \\
&= \mu(f) \, \mathcal{R} [(\nabla f)(\mathcal{R}^2\mathbf{r})] \\
&= \mu(f) \, \mathcal{R} (\nabla f)(\mathbf{r}), \quad \square
\end{aligned}
$$

Alternatively, one can also first derive the symmetry of the scalar differential operators $$\partial_i$$:

$$
\begin{aligned}
\mu(\partial_1 f) = \mu(\partial_x f) &= \mu(f), \\
\mu(\partial_2 f) = \mu(\partial_y f) &= \mu(f), \\
\mu(\partial_3 f) = \mu(\partial_z f) &= -\mu(f)
\end{aligned}
$$

These operators can then be formally treated as normal scalars and assigned their own symmetry, i.e. $$\partial_1,\partial_2 \in \mathcal{S}$$, hence $$\mu(\partial_1) = \mu(\partial_2) = 1$$ , and $$\partial_3 \in \mathcal{A}$$, hence $$\mu(\partial_3)=-1$$. The operator $$\nabla$$ can be formally treated as a normal vector with $$\nabla\in \mathcal{S}_1$$ or $$\mu(\nabla) = 1$$. Using these formal treatments, $$\nabla f$$ is just a scalar-vector product. Applying known properties, we have

$$
\mu(\nabla f) = \mu(\nabla) \, \mu(f) = \mu(f).
$$

<br />

### Vector divergence

Divergence of a(n) symmetric (resp. anti-symmetric) vector field produces a(n) symmetric (resp. anti-symmetric) scalar field. In summary,

$$
\mu(\nabla\cdot \mathbf{f}) = \mu(\mathbf{f})
$$

A proof can be given by combining the formal treatment $$\mu(\nabla) = 1$$ and the vector inner product property $$\mu(\mathbf{f}\cdot \mathbf{g}) = \mu(\mathbf{f})\, \mu(\mathbf{g})$$. Alternatively, this can be proven using vector identities and chain rules.


<br />

### Vector curl

Curl of a(n) symmetric (resp. anti-symmetric) vector field produces an(a) anti-symmetric (resp. symmetric) vector field. In summary,

$$
\mu(\nabla\times \mathbf{f}) = - \mu (\mathbf{f})
$$

A proof can be given by combining the formal treatment $$\mu(\nabla) = 1$$ and the vector cross product property $$\mu(\mathbf{f}\times \mathbf{g}) = - \mu(\mathbf{f})\, \mu(\mathbf{g})$$. Alternatively, this can be proven using vector identities and chain rules.


<br />

### Vector contraction with vector gradient

Contraction of a(n) symmetric (anti-symmetric) vector field with the gradient of a(n) symmetric (anti-symmetric) vector field produces a symmetric vector field. Vice versa, contraction of a(n) symmetric (anti-symmetric) vector field with the gradient of an(a) anti-symmetric (symmetric) vector field produces an anti-symmetric vector field. In summary,

$$
\mu(\mathbf{f}\cdot \nabla \mathbf{g}) = \mu(\mathbf{f}) \, \mu(\mathbf{g})
$$

A proof can be given by combining the formal treatment $$\mu(\nabla) = 1$$ and

$$
\mu((\mathbf{f}\cdot \mathbf{g})\mathbf{h}) = \mu(\mathbf{f})\, \mu(\mathbf{g})\, \mu(\mathbf{h}).
$$

Alternatively, this can be proven using vector identities and chain rules.


<br />

### Dyadic / tensor product

The tensor product of two vectors also have certain properties of reflectional symmetry, if the two vectors themselves have reflectional symmetry. However, this also relies on a definition for reflectional symmetry of tensors. For rank-2 tensor $$\mathbf{T}$$, we can further introduce definition

$$
\begin{aligned}
\mathcal{S}_2 &= \{\mathbf{T}:\ \mathbf{T}(\mathbf{r}) = \mathcal{R} \, \mathbf{T}(\mathcal{R}\mathbf{r}) \, \mathcal{R} \quad \forall \mathbf{r}\in \mathbb{R}^3 \}, \\
\mathcal{A}_2 &= \{\mathbf{T}:\ \mathbf{T}(\mathbf{r}) = -\mathcal{R} \, \mathbf{T}(\mathcal{R}\mathbf{r})\, \mathcal{R} \quad \forall \mathbf{r}\in \mathbb{R}^3\}
\end{aligned}
$$

where $$\mathcal{R} \mathbf{T} \mathcal{R}$$ indicates applying the reflection operator both to the left and to the right of the tensor. In this case, the tensor product of two symmetric (anti-symmetric) vectors is a symmetric dyad, whereas the tensor product of one symmetric and one anti-symmetric vector is an anti-symmetric dyad. In summary,

$$
\mu(\mathbf{f}\otimes \mathbf{g}) = \mu(\mathbf{f}) \, \mu(\mathbf{g})
$$

***Proof***: using component form, if $$\mathbf{T} = \mathbf{f}\otimes \mathbf{g}$$, then

$$
\begin{aligned}
T_{ij}(\mathcal{R}\mathbf{r}) &= f_i(\mathcal{R}\mathbf{r}) \, g_j(\mathcal{R}\mathbf{r}) \\
&= [\mu(f_i) f_i(\mathbf{r})] \, [\mu(g_j) g_j(\mathbf{r})] \\
&= [\mu(\mathbf{f}) \mathcal{R}_i f_i(\mathbf{r})] \, [\mu(\mathbf{g}) \mathcal{R}_j g_j(\mathbf{r})] \\
&= [\mu(\mathbf{f}) \mu(\mathbf{g})] \mathcal{R}_i \mathcal{R}_j f_i(\mathbf{r}) g_j(\mathbf{r}) \\
&= [\mu(\mathbf{f}) \mu(\mathbf{g})] \mathcal{R}_i \mathcal{R}_j T_{ij}(\mathbf{r}) \\
\mathbf{T}(\mathcal{R}\mathbf{r}) &= [\mu(\mathbf{f}) \mu(\mathbf{g})] \, \mathcal{R}\mathbf{T}(\mathbf{r})\mathcal{R}. \quad \square
\end{aligned}
$$

<br />

### Vector gradient

The gradient of a(n) symmetric (resp. anti-symmetric) vector is a(n) symmetric (resp. anti-symmetric) rank-2 tensor. In summary,

$$
\mu(\nabla \mathbf{f}) = \mu (\mathbf{f})
$$

This can be similar shown using the tensor product rule and the formal treatment $$\mu(\nabla) = 1$$.


<br />



