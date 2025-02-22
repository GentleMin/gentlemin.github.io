---
layout: page
title: Vector representation on a sphere
description: Helmholtz representation, Mie representation, etc.
importance: 1
date: 2023-02-10 22:12:00-0400
category: Maths
toc:
  sidebar: left
---

Here I compile a self-contained description of vector field representation and decomposition, and differential operator on a sphere.

The key point I am trying to address (and understand) the so-called ***Mie representation***, also referred to as the ***toroidal-poloidal decomposition***. It was likely first introduced by **Gustav Mie** in 1908 to discuss the Maxwell's equations in a sphere. At different times, **Horace Lamb** and **A.E.H. Love** used part of related concepts. In the 1950s, **Walter Elsasser** began to use this decomposition for studying dynamo models, and termed the two terms ***toroidal*** and ***poloidal***. Probably due to Elsasser's introduction, the geodynamo community favours the name toroidal-poloidal decomposition, while the rest of geomagnetism community seems to use the term Mie representation.

The mathematical foundation of such representations/decompositions is well developed. In the 1950s, **W.V.D. Hodge** formally proved the existence of Helmholtz representation, and **George Backus** provided proof for existence and uniqueness of Mie representation shortly afterwards. A nice review on Mie representation, see [Backus, 1986](https://doi.org/10.1029/RG024i001p00075). The review also contains an entire section on operator algebra, which is a nice reference for generalizing vector/tensor identities to general operators. An alternative perspective starts from Helmholtz representation theorem and so-called vector spherical harmonic basis. This is the tool used e.g. by **Dahlen and Tromp** ([1999](https://www.degruyter.com/document/doi/10.1515/9780691216157/html)) to study normal oscillations, and this approach is taken by [Sabaka et al., 2010](https://doi.org/10.1007/978-3-642-01546-5_17) to provide an introductory and concise discussion on treatment of non-potential fields.

The content in this note is extensively used for decomposing and differentiating vectors in spherical geometry, i.e. on a spherical manifold embedded in the Euclidean space. Therefore, (vector) differential operators in spherical coordinates will be repeatedly used. For a self-contained note on such operators, see [[Orthogonal Curvilinear Frames]].

---
## Operators on spherical surface

In a spherical frame, any vector can be decomposed into a radial component and a sphere-tangent component (tangent to the surface of the sphere):

$$
\mathbf{A} = \mathbf{A}_r + \mathbf{A}_s = A_r \mathbf{e}_r + (\mathbf{A} - A_r \mathbf{e}_r) = \mathbf{e}_r(\mathbf{e}_r\cdot \mathbf{A}) + (\mathbf{A} - \mathbf{e}_r(\mathbf{e}_r\cdot \mathbf{A})) = \mathbf{e}_r \mathbf{e}_r \cdot \mathbf{A} + (\mathbf{I} - \mathbf{e}_r \mathbf{e}_r) \cdot \mathbf{A}
$$

which is analog to the projection operator and its orthogonal complement in the high-dimensional space ($$\mathbf{X}\mathbf{X}^\dagger$$ and $$\mathbf{I} - \mathbf{X}\mathbf{X}^\dagger$$). Also analogous to the general orthogonal projections, we immediately have the radial fields and the tangent field are perpendicular to each other in 3-D space, i.e. 

$$\mathbf{A}_s\cdot \mathbf{A}_r = 0.$$

The surface nabla operator $$\nabla_s$$ is defined as the dimensionless angular portion of the nabla operator, i.e. the nabla operator excluding the radial part:

$$
\nabla_s = r \nabla - \mathbf{r}\frac{\partial}{\partial r} = r \nabla  - \mathbf{r}(\mathbf{e}_r \cdot \nabla).
$$

Here we take the form defined in [Sabaka et al., 2010](https://doi.org/10.1007/978-3-642-01546-5_17). [Backus, 1986](https://doi.org/10.1029/RG024i001p00075) uses the dimensional form for $$\nabla_s$$, but redefines a new dimensionless form $$\nabla_i$$. The definition is elegant in the sense that it consistently yields three first-order differential operators on the spherical surface. It is called the surface operator because it operates on any field that is defined on the surface, even without any information as to what the field is like in the vicinity radii (also evident from the explicit forms in spherical coordinates, shown below). In this section I introduce their definitions and properties.

### Surface gradient
The surface gradient is

$$
\nabla_s f = r\nabla f - \mathbf{r}\frac{\partial f}{\partial r} = \frac{\partial f}{\partial \theta}\mathbf{e}_\theta + \frac{1}{\sin\theta} \frac{\partial f}{\partial \phi}\mathbf{e}_\phi.
$$

Since it is only relevant to angular coordinates, and $$\partial_r \mathbf{e}_r = \partial_r \mathbf{e}_\theta = \partial_r \mathbf{e}_\phi = 0$$, the surface gradient commutes with radial differentiation

$$
\nabla_s \frac{\partial}{\partial r} = \frac{\partial}{\partial r} \nabla_s
$$

It is obvious and intuitively correct that the radius of position vector has trivial surface gradient (i.e. as the position moves along the spherical surface, there is not change whatsoever in its radius)

$$
\nabla_s r = 0,
$$

therefore $$\nabla_s$$ commutes with $$r$$ as an operator. [Backus, 1986](https://doi.org/10.1029/RG024i001p00075) has actually introduced $$F^M$$ to denote the multiplication operator of field $$F$$ (e.g. when $$\nabla F^M$$ operates on $$G$$, it is interpreted as $$\nabla (F^M(G))$$, rather than $$(\nabla F) G$$). When the surface gradient acts upon a unit position vector, we obtain the ***surface identity tensor***, which is the orthogonal projection operator unto the tangent space of the sphere:

$$
\nabla_s \hat{\mathbf{r}} = r\nabla\left(\frac{\mathbf{r}}{r}\right) - \mathbf{r} \frac{\partial}{\partial r}\hat{\mathbf{r}} = \nabla \mathbf{r} - \mathbf{r}\frac{\nabla r}{r^2} - 0 = \mathbf{I} - \hat{\mathbf{r}}\hat{\mathbf{r}} =  \mathbf{I} - \mathbf{e}_r \mathbf{e}_r,
$$

and therefore

$$
\mathbf{A}\cdot \nabla_s \hat{\mathbf{r}} = \mathbf{A}\cdot (\mathbf{I} - \mathbf{e}_r\mathbf{e}_r) = \mathbf{A}_s.
$$

Last but not least, surface gradient, as its name suggests, is tangent to the spherical surface. Therefore, projecting the gradient to the radial direction always gives zero

$$
\hat{\mathbf{r}}\cdot \nabla_s \equiv 0.
$$

The surface gradient introduced as such is also proportional (with a $$r$$ prefactor) to the actual gradient on a spherical surface as a Riemann manifold (see [[Orthogonal Curvilinear Frames]], on this 2-D surface $$h_1 = r, h_2 = r\sin\theta$$). Therefore, the directional derivative in any surface-tangent direction is given by

$$
\frac{\partial f}{\partial \nu} = \nu\cdot \nabla_sf \qquad (\nu \cdot \mathbf{r}=0)
$$

and the integral form

$$
f(\mathbf{r}_2) - f(\mathbf{r}_1) = \int_{\mathbf{r}_1}^{\mathbf{r}_2} d\mathbf{l} \cdot \nabla_s f.
$$

Here $$\mathbf{r}_2$$ and $$\mathbf{r}_1$$ are on the same spherical surface (same radius). Following this logic the definition for "irrotational" and "potential" ("consoidal" in [Backus, 1986](https://doi.org/10.1029/RG024i001p00075)) vector field is straightforward

$$
\oint_C d\mathbf{l}\cdot \mathbf{A}_s \equiv 0 \quad \forall C \in S(r) \qquad \Longleftrightarrow \qquad \exists f, \, s.t.\, \mathbf{A}_s = \nabla_s f.
$$

### Surface divergence
The so-called surface divergence is

$$
\nabla_s\cdot \mathbf{A} = r \nabla\cdot \mathbf{A} - \mathbf{r} \cdot \frac{\partial}{\partial r} = 2A_r + \frac{1}{\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta A_\theta) + \frac{1}{\sin\theta} \frac{\partial A_\phi}{\partial\phi}
$$

where we already uses the fact that $$\partial_r \mathbf{e}_r = \partial_r \mathbf{e}_\theta = \partial_r \mathbf{e}_\phi = 0$$. Let $$\mathbf{A} = \hat{\mathbf{r}}$$, i.e. $$A_r = 1$$ and $$A_\theta=A_\phi =0$$, we have the surface divergence of unit position vector

$$
\nabla_s \cdot \hat{\mathbf{r}} = 2.
$$

Despite the name, the surface divergence is not really, and not even proportional to, the divergence on the sphere as a 2-D Riemann manifold (this is perhaps why Backus did not use the term "surface divergence"; however, Sabaka et al. did use this term). The latter can be derived directly using results from [[Orthogonal Curvilinear Frames]], which has the form

$$
\nabla_{m}\cdot \mathbf{A} = \frac{1}{h_1h_2} \left(\partial_1 (h_2A_1) + \partial_2(h_1 A_2)\right) = \frac{1}{r\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta A_\theta) + \frac{1}{r\sin\theta} \frac{\partial A_\phi}{\partial\phi}
$$

with $$m$$ denoting on a manifold. The result is obviously void of $$A_r$$, as on a 2-D manifold there is no $$A_r$$ anyway. From this we can conclude that $$\nabla_s \cdot \mathbf{A} = 2A_r + r\nabla_{m}\cdot \mathbf{A}$$. The true divergence on a sphere satisfies Gauss theorem

$$
\int_{\sigma(S)} \nabla_m \cdot \mathbf{A} \, dS = \oint_{\partial\sigma(S)} \mathbf{A}\cdot \hat{\mathbf{n}} \, dl
$$

where $$\sigma$$ is a patch on the sphere $$S$$, $$\partial \sigma$$ is the closed curve on the sphere that borders $$\sigma$$ (i.e. its boundary), and $$\hat{\mathbf{n}}$$ the outer normal direction for any point on the boundary. In particular, if we consider the divergence of a smooth vector field on a whole sphere

$$
\oint_S \nabla_m\cdot \mathbf{A} \, dS = \int_{S^+} \nabla_m \cdot \mathbf{A} \, dS + \int_{S^-} \nabla_m \cdot \mathbf{A} \, dS = \oint_C\mathbf{A}\cdot \hat{\mathbf{n}}^+\, dl + \oint_C\mathbf{A}\cdot \hat{\mathbf{n}}^-\, dl = 0
$$

where we split the sphere $$S$$ into two hemispheres $$S^+$$ and $$S^-$$, who obviously share the same boundary $$C$$, but have negative outer normals $$\mathbf{n}^+$$ and $$\mathbf{n}^-$$. Therefore the integral of the divergence on a spherical surface manifold always vanishes. This is analogous to the Cartesian case where the vector field either has compact support or converges to zero at a rate faster than $$1/r^2$$ in 3-D. However, on a sphere, no additional constraint on $$\mathbf{A}$$ except for smoothness is required, as the geometry of the manifold is fundamentally different.
The previous property can also be explicitly proved using spherical coordinates

$$
\oint_S \nabla_m\cdot \mathbf{A}\, dS = r\int_0^{2\pi}d\phi \int_0^{\pi} \frac{\partial}{\partial\theta} (\sin\theta A_\theta)\,d\theta + r\int_0^\pi d\theta \int_0^{2\pi} \frac{\partial A_\phi}{\partial \phi} d\phi = 0
$$

which is guaranteed as long as $$\mathbf{A}$$ is smooth and regular at poles. Finally, the surface divergence will have integrals:

$$
\int_{\sigma(S)} \nabla_s\cdot \mathbf{A} \, dS = 2\int_{\sigma(S)}A_r \, dS + r\oint_{\partial\sigma} \mathbf{A}\cdot \hat{\mathbf{n}}\, dl, \quad \int_S \nabla_s\cdot \mathbf{A}\, dS = 2\int_S A_r \, dS.
$$

Of course, when we restrict to tangential field only on the sphere, we have $$\nabla_s\cdot \mathbf{A}_s = r \nabla_m\cdot \mathbf{A}_s$$, and all the additional terms concerning $$A_r$$ would naturally vanish.
Defining the spherical surface average (which is a function of radius $$r$$) as

$$
\langle f \rangle_S = \frac{1}{4\pi r^2} \oint_S f \, dS
$$

The relations can be written as

$$
\langle \nabla_m\cdot \mathbf{A} \rangle_S = 0,\quad \langle \nabla_s\cdot \mathbf{A} \rangle_S = 2\langle A_r\rangle_S.
$$

Now we have introduced the spherical surface average, it might be benefitial to know that the averaging commutes with any fields that are functions of $$r$$ only

$$
g(r)\langle f(\mathbf{r})\rangle_S = \langle g(r)f(\mathbf{r})\rangle_S.
$$

It can be shown further that spherical averaging also commutes with radial differentiation. To see this one needs to note that the integration surface is also a function of $$r$$, and so

$$
\begin{aligned}
\partial_r \langle f\rangle_S &= \partial_r \left(\frac{1}{4\pi r^2}\oint_S f(\mathbf{r})\, dS\right) = \langle \partial_r f\rangle_S + \partial_r\left(\frac{1}{4\pi r^2}\right)\oint_S f\, dS + \frac{1}{4\pi r^2} \oint_S f\, \partial_r dS \\
&= \langle \partial_r f\rangle_S - \frac{1}{2\pi r^3}\oint_S f\, dS + \frac{1}{4\pi r^2}\oint_S f \, \frac{2}{r} dS = \langle \partial_r f\rangle_S,
\end{aligned}
$$

where we used $$\partial_r dS = \partial_r (r^2\sin\theta d\theta d\phi) = 2r\sin\theta d\theta d\phi = (2/r)dS$$. Therefore we can conclude that any operator that only contains $$r$$ and the differentiation of $$r$$ commutes with spherical averaging.

### Surface curl
We use the definition in [Sabaka et al., 2010](https://doi.org/10.1007/978-3-642-01546-5_17) here. The surface curl is defined as

$$
\Lambda_s\cdot  \mathbf{A} = \mathbf{e}_r\cdot\nabla_s\times\mathbf{A}.
$$

$$\Lambda_s$$ is a vector operator, and its contraction with any vector field yields the surface curl of the field. It is shown in Backus 1986 that the cross product of vectors can also be expressed as tensor-vector contraction, hence there is no problem in writing this definition. **Note surface curl is a scalar**, which is understandable since we are considering the rotational property on a 2-D Riemann manifold.

There are many equivalent forms for the surface curl. Using the fact that $$\nabla \times \mathbf{r} = 0$$, $$\nabla_s\times \hat{\mathbf{r}} = 0$$, and the operator identity $$\mathbf{K}\cdot (\mathbf{L}\times \mathbf{M}) = (\mathbf{K} \times \mathbf{L}) \cdot \mathbf{M}$$  introduced in [Backus, 1986](https://doi.org/10.1029/RG024i001p00075), the surface curl operator can be defined as

$$
\begin{aligned}
\Lambda_s \cdot \mathbf{A} &= \hat{\mathbf{r}}\cdot \nabla_s \times \mathbf{A} = (\hat{\mathbf{r}}^M \times \nabla_s) \cdot \mathbf{A} \\
&= \mathbf{r} \cdot \nabla \times \mathbf{A} = (\mathbf{r}^M \times \nabla) \cdot \mathbf{A} \\
&= -\nabla_s \cdot (\hat{\mathbf{r}} \times \mathbf{A})= -(\nabla_s \times \hat{\mathbf{r}}^M) \cdot \mathbf{A} \\
&= -\nabla \cdot (\mathbf{r} \times \mathbf{A})= -(\nabla \times \mathbf{r}^M) \cdot \mathbf{A}
\end{aligned}
$$

The $$M$$ superscript should be interpreted as multiplication operators (see sect on surface gradient). In the equation above, the expressions on the right column has the form of an inner product, and thus can be directly used to define the surface curl.
In spherical coordinates, the vector operator has the explicit form

$$
\begin{aligned}
\Lambda_s &= - \mathbf{e}_\theta \frac{1}{\sin\theta}\frac{\partial}{\partial \phi} + \mathbf{e}_\phi \frac{\partial}{\partial \theta} \\
\Lambda_s\cdot \mathbf{A} &= \frac{1}{\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta A_\phi) - \frac{1}{\sin\theta} \frac{\partial A_\theta}{\partial \phi} = \Lambda_s\cdot \mathbf{A}_s.
\end{aligned}
$$

Apparently the surface curl, just like $$\nabla_s$$, only has angular components. Therefore, projection onto the radial component is zero, same as $$\nabla_s$$. Hence we have identities when multiplied by $$\hat{\mathbf{r}}$$:

$$
\hat{\mathbf{r}}\cdot \Lambda_s = \hat{\mathbf{r}}\cdot (\hat{\mathbf{r}}\times \nabla_s) = 0,\quad \hat{\mathbf{r}}\times \Lambda_s = \hat{\mathbf{r}}\times(\hat{\mathbf{r}} \times \nabla_s) = -\nabla_s.
$$

The surface curl, just like $$\nabla_s$$, commutes with any operators/fields that are only dependent upon $$r$$:

$$
\Lambda_sf(r) = f(r)\Lambda_s,\quad \Lambda_s \frac{\partial}{\partial r} = \frac{\partial}{\partial r}\Lambda_s,
$$

Some additional properties concerning $$\Lambda_s$$:

$$
\begin{aligned}
\nabla_s\times(\hat{\mathbf{r}}\times \mathbf{A}) &= \hat{\mathbf{r}}(\nabla_s\cdot \mathbf{A}_s) - \hat{\mathbf{r}} \cdot \nabla_s \mathbf{A}_s + \mathbf{A}_s\cdot\nabla_s \hat{\mathbf{r}} - \mathbf{A}_s (\nabla_s\cdot \hat{\mathbf{r}}) = \hat{\mathbf{r}}(\nabla_s\cdot \mathbf{A}_s) - \mathbf{A}_s \\
\Lambda_s\cdot (\hat{\mathbf{r}} \times \mathbf{A}) &= \hat{\mathbf{r}}\cdot \nabla_s\times(\hat{\mathbf{r}}\times \mathbf{A}) =  \nabla_s\cdot \mathbf{A}_s \\[1em]
\nabla\cdot \Lambda_s &= - \nabla \cdot (\nabla \times \mathbf{r}^M) = - (\nabla \times \nabla) \cdot \mathbf{r}^M = 0 \\
\nabla_s\cdot \Lambda_s &= (r\nabla - \mathbf{r}\partial_r)\cdot \Lambda_s = r\nabla\cdot \Lambda_s - \mathbf{r}\cdot \Lambda_s\partial_r = 0 \\
\Lambda_s \cdot \nabla &= \mathbf{r}\cdot (\nabla\times \nabla) = 0\\
\Lambda_s\cdot \nabla_s &= \Lambda_s\cdot (r \nabla - \mathbf{r}\partial_r) = r\Lambda_s\cdot \nabla - \Lambda_s\cdot \mathbf{r} \partial_r = 0 \\[1em]
\nabla_s\times \Lambda_s f &= \nabla_s\times (\hat{\mathbf{r}}\times \nabla_s f) = \hat{\mathbf{r}}(\nabla_s\cdot \nabla_s f) - \nabla_s f\\
\Longrightarrow &\quad \nabla_s\times \Lambda_s = \hat{\mathbf{r}}(\nabla_s\cdot \nabla_s) - \nabla_s \\
\Lambda_s\cdot \Lambda_sf &= \Lambda_s\cdot (\hat{\mathbf{r}}\times \nabla_s f) = \nabla_s\cdot \nabla_s f \\
\Longrightarrow &\quad \Lambda_s\cdot \Lambda_s = \nabla_s\cdot \nabla_s
\end{aligned}
$$

We can already see that since $$\Lambda_s$$ has the operator form

$$
\Lambda_s = -\nabla \times \mathbf{r}^M = - \nabla_s \times \hat{\mathbf{r}}^M
$$

it follows that $$\Lambda_s$$ generates a toroidal field from a scalar field $$f$$. Conversely, a toroidal field is nothing but $$\Lambda_s$$ operated on some scalar $$f$$.

The surface curl proves to be the dimensionless form of the actual curl on the corresponding surface of the sphere, which can be derived using exterior differentiation

$$
\mathrm{rot} \mathbf{A}_s = \nabla_m\times \mathbf{A}_s = \frac{1}{h_1h_2}\left(\partial_1(h_2A_2) - \partial_2(h_1A_1)\right) = \frac{1}{r\sin\theta} \left[\frac{\partial}{\partial\theta}(\sin\theta A_\phi) - \frac{\partial A_\theta}{\partial \phi}\right] = \frac{1}{r} \Lambda_s\cdot \mathbf{A}_s
$$

On the surface of the sphere, the true curl fulfills Stoke's theorem

$$
\int_{\sigma(S)} \mathrm{rot}\mathbf{A}_s \, dS = \int_\sigma \nabla_m\times \mathbf{A}_s \, dS = \oint_{\partial \sigma} \mathbf{A}_s\cdot d\mathbf{l}
$$

hence the theorem for the dimensionless surface curl has the form

$$
\int_\sigma \Lambda_s\cdot \mathbf{A}_s\, dS = r\oint_{\partial \sigma} \mathbf{A}_s \cdot d\mathbf{l}.
$$

Following the same logic (e.g. on the whole surface of a sphere, the integration area can be cut into two hemispheres, and the resulting line integrals cancel out), the curl will integrate to zero

$$
\oint_S \Lambda_s\cdot \mathbf{A}_s\, dS \equiv 0 \quad \Longrightarrow \quad \langle \Lambda_s \cdot \mathbf{A}_s\rangle_{S} \equiv 0.
$$

Backus uses integral of surface curl to introduce the Gauss theorem for the divergence. However the latter is consistently introduced after the divergence on the surface is properly defined. In addition, one can prove $$\Lambda_s f$$ (note this is a vector now) has zero surface integral, by selecting an arbitrary direction as the pole $$\hat{\mathbf{z}}$$ 

$$
\hat{\mathbf{z}}\cdot \oint_S \Lambda_s f\, dS = \oint_S \hat{\mathbf{z}}\cdot \Lambda_s f\, dS = \oint_S \frac{\partial}{\partial \phi}f\, dS \equiv 0\quad \Longrightarrow\quad \oint_S \Lambda_s f\, dS \equiv \mathbf{0}, \quad \langle \Lambda_s f\rangle_S = \mathbf{0}.
$$

### Field properties on a sphere
Consider a patch on the surface of the sphere, denoted as $$P(b) \in S(b)$$. We have already introduced a (surface) ***potential/consoidal*** field, which can be written as a [[#Surface gradient]]

$$
\mathbf{A}_s = \nabla_s f,
$$

an (surface) ***irrotational*** field, whose line integral on any closed curve in $$P$$ vanishes

$$
\oint_C \mathbf{A}_s\cdot d\mathbf{l} = 0,\quad \forall C\in P(b),
$$

which is equivalent to potential/consoidal. Now from the the Stoke's theorem, we see a (surface) ***curl-free*** field is another synonym for an irrotational field, hence potential field

$$
\Lambda_s\cdot \mathbf{A}_s=0,\,\forall \mathbf{r}\in P(b) \quad \Longleftrightarrow \quad \oint_C\mathbf{A}_s\cdot d\mathbf{l}=0,\, \forall C\in P(b)\quad \Longleftrightarrow \quad \exists f,\, \mathbf{A}_s = \nabla_s f
$$

There is one more equivalence using identities concerning the surface divergence. First a (surface) ***solenoidal*** or **divergence-free** field

$$
\nabla_s\cdot \mathbf{A}_s = 0,\quad \forall \mathbf{r}\in P(b)\quad \Longleftrightarrow \quad \Lambda_s\cdot (\hat{\mathbf{r}}\times \mathbf{A}_s)= -\nabla_s \cdot \mathbf{A}_s = 0
$$

is equivalent to stating $$\hat{\mathbf{r}}\times \mathbf{A}_s$$ is irrotational/curl-free/potential. Again using the identity, it is so *iff* $$\mathbf{A}_s$$ is a ***toroidal*** field, i.e.

$$
\hat{\mathbf{r}}\times \mathbf{A}_s = \nabla_s f \quad \Longleftrightarrow \quad \nabla_s f = -\hat{\mathbf{r}}\times \Lambda_s f, \, \mathbf{A}_s=-\Lambda_s f = \Lambda_s(-f).
$$

### Surface Laplacian
The surface Laplacian is defined as

$$
\begin{aligned}
\nabla_s^2 = \nabla_s\cdot \nabla_s &= r\nabla_s\cdot \nabla - r\nabla_s\cdot \hat{\mathbf{r}} \partial_r \\
&= r^2\nabla\cdot \nabla - r^2 \hat{\mathbf{r}}\partial_r\cdot \nabla - r^2\nabla\cdot \hat{\mathbf{r}}\partial_r + r^2 \hat{\mathbf{r}}\partial_r\cdot \hat{\mathbf{r}}\partial_r \\
&= r^2 \nabla^2 - r^2\partial_r \hat{\mathbf{r}}\cdot \nabla - r^2\hat{\mathbf{r}}\cdot \nabla \partial_r - r^2(\nabla\cdot \hat{\mathbf{r}})\partial_r + r^2\partial_r\hat{\mathbf{r}}\cdot \hat{\mathbf{r}}\partial_r \\
&= r^2 \left(\nabla^2 - \partial_r\partial_r - \partial_r\partial_r - (2/r)\partial_r+\partial_r\partial_r\right)\\
&= r^2\nabla^2 - \partial_r(r^2\partial_r),\\
\nabla^2 = \nabla\cdot \nabla &= \frac{1}{r^2}\frac{\partial}{\partial r} \left(r^2 \frac{\partial}{\partial r}\right) + \frac{1}{r^2}\nabla_s^2.
\end{aligned}
$$

and is hence simply the angular part of the Laplacian in spherical coordinates

$$
\nabla_s^2 = \frac{1}{\sin\theta} \frac{\partial}{\partial \theta} \left( \sin\theta \frac{\partial}{\partial \theta} \right) + \frac{1}{\sin^2 \theta} \frac{\partial^2}{\partial \phi^2} = r^2 \nabla^2  - \frac{\partial}{\partial r}r^2 \frac{\partial}{\partial r},\quad \nabla^2 = \frac{1}{r^2}\frac{\partial}{\partial r}r^2 \frac{\partial}{\partial r} + \frac{1}{r^2}\nabla_s^2.
$$

The surface Laplacian has commutation property which it inherits from $$\nabla_s$$

$$
\nabla_s^2f^M(r) = f(r)\nabla^2,\qquad \nabla_s^2 \partial_r = \partial_r \nabla_s.
$$

Therefore, the surface Laplacian simply commutes with the whole Laplacian

$$
\nabla_s^2 \nabla^2 = \nabla^2 \nabla_s^2.
$$

Using the formulae for integral of [[#Surface divergence]], and taking into account that $$\nabla_s f$$ is tangent to the sphere surface, i.e. no $$\mathbf{e}_r$$ component, then

$$
\int_{\sigma(S)} \nabla_s^2 f \, dS = r\int_{\partial \sigma(S)} \nabla_s f \cdot \hat{\mathbf{n}} \,dl, \quad \oint_S \nabla_s^2 f\, dS\equiv 0, \quad \langle \nabla_s^2f\rangle_S \equiv 0.
$$

This property yields the following useful corollary (note commutation of spherical averaging)

$$
\langle \nabla^2 f \rangle_S = \frac{1}{r^2}\frac{d}{dr} \left[r^2 \frac{d}{dr} \langle f \rangle_S \right]
$$

Surface Laplacian gives rise to the surface Poisson equation

$$
\nabla_s^2 g = f
$$

which is essential in vector representations (since often the potentials are constructed by solving the surface Possion eqn). Such Laplacian can be established for arbitrary Riemann manifolds.
For manifolds in the shape of a closed surface with a finite number of "doughnut holes" (Backus, 1986), the existence and uniqueness of solution is guaranteed by the extra constraint

$$
\langle g\rangle_s = 0,\qquad \langle f\rangle_s = 0.
$$

The former condition guarantees uniqueness of the solution, if any. This is easily seen as

$$
\nabla_s^2(g+C) = \nabla_s^2g
$$

therefore the solution holds with addition of arbitrary constant field on the surface. Conversely, if fields $$g_1$$ and $$g_2$$ are solutions, they are separated by a constant field

$$
\begin{aligned}
\nabla_s^2(g_1 - g_2) = \nabla_s^2 \delta g=0\quad &\Longrightarrow \quad \nabla_s\cdot (\delta g\nabla_s\delta g) = |\nabla_s\delta g|^2\\
\oint_S \nabla_s \cdot (\delta g\nabla_s\delta g)\, dS = \oint_S |\nabla_s\delta g|^2\, dS \equiv 0 \quad &\Longrightarrow \quad \nabla_s\delta g\equiv 0,\quad \forall \mathbf{r}\in S\quad \Longrightarrow \quad \delta g = C
\end{aligned}
$$

The latter condition is easily seen as a necessary condition since $$\langle \nabla_s^2 g\rangle_S = 0$$ is always true. It is also a sufficient condition, which guarantees the existence of solution. This is proved in three ways **for spherical surfaces only** in [Backus, 1986](https://doi.org/10.1029/RG024i001p00075), most straightforwardly using spherical harmonics. Here I omit the proof, but simply comment on the fact that spherical harmonics are eigenfunctions of the spherical surface Laplacian:

$$
\nabla_s^2 \, Y_l^m(\theta,\phi) = -l(l+1) \, Y_l^m(\theta, \phi).
$$

In some literature (e.g. from the geodynamo community, but also in [Dahlen and Tromp, 1999](https://www.degruyter.com/document/doi/10.1515/9780691216157/html)), the negative surface Laplacian is also termed the angular momentum operator

$$
\mathcal{L}^2 = -\nabla_s^2,\quad \mathcal{L}^2Y_l^m = l(l+1)Y_l^m.
$$

This convention obviously comes from quantum mechanics, where such operator actually yields the spin of a particle. It has no specific physical meaning in the context of either fluid mechanics or electromagnetics.
As a final remark, we collect here the expression for the spherical surface Laplacian in Cartesian coordinates, 

$$
\begin{aligned}
\nabla_s^2 &= r^2 \nabla^2 - \partial_r(r^2\partial_r) = r^2\nabla^2 - \sum_i \left(\frac{\partial x_i}{\partial r} \partial_i\right)r^2\sum_j\left(\frac{\partial x_j}{\partial r}\partial_j\right) \\
&= r^2\nabla^2 - \sum_i\left(\frac{x_i}{r}\partial_i\right)\sum_j\left(rx_j\partial_j\right) \\
&= r^2\nabla^2 - \sum_i \frac{x_i^2}{r^2}\sum_j x_j\partial_j - \sum_ix_i\partial_i \sum_j x_j\partial_j \\
&= r^2\nabla^2 - \sum_j x_j\partial_j - \sum_i x_j\partial_j \sum_jx_j\partial_j,
\end{aligned}
$$

which will become useful when deriving the commutation relation with Cartesian coordinate differentiations. Roberts ([1968](https://doi.org/10.1098/rsta.1968.0007)) attempts to give this expression, but his equation (2.7) is wrong.

---
## Helmholtz representation

Having introduced the surface operators, we are now in a place to investigate the vector representation on a (spherical) surface. Given a tangent vector $$\mathbf{A} = \mathbf{A}_s$$ on the sphere $$S(b)$$, it can always be decomposed into a consoidal field and a toroidal field,

$$
\mathbf{A} = \mathbf{A}_c + \mathbf{A}_T = \nabla_s g + \Lambda_s h = \nabla_s g + \nabla_s\times h\hat{\mathbf{r}}
$$

where the small $$c$$ subscript denotes consoidal, and $$T$$ denotes toroidal. This is referred to as the ***Helmholtz representation of vectors on a sphere***. Taking the surface divergence and the surface curl respectively, the equation yields

$$
\begin{aligned}
\nabla_s\cdot \mathbf{A} &= \nabla_s\cdot \nabla_s g+ \nabla_s\cdot \Lambda_sh=\nabla_s^2g + 0= \nabla_s^2g \\
\Lambda_s\cdot \mathbf{A} &= \Lambda_s\cdot \nabla_s g + \Lambda_s\cdot \Lambda_sh= 0 + \nabla_s^2h= \nabla_s^2h
\end{aligned}
$$

Therefore $$g$$ and $$h$$ are solutions to the surface Poisson equation, with $$\nabla_s\cdot \mathbf{A}$$ and $$\Lambda_s\cdot \mathbf{A}$$ as right hand sides. Since for a tangent vector field, the following conditions are already satisfied

$$
\langle \nabla_s\cdot \mathbf{A} \rangle_S \equiv 0,\quad \langle \Lambda_s\cdot \mathbf{A} \rangle_S \equiv 0,
$$

it follows from the existence of solution to surface Poisson equation that the solutions for $$g$$ and $$h$$ exist, hence the decomposition exists. The decomposition is apparently unique when we further require $$\langle g\rangle_S = \langle h\rangle_S = 0$$.
If we define inner product of vector fields on the sphere

$$
\langle\mathbf{A},\mathbf{B} \rangle_S = \frac{1}{4\pi r^2}\oint_S \bar{\mathbf{A}}\cdot \mathbf{B}\, dS = \langle \bar{\mathbf{A}}\cdot \mathbf{B}\rangle_S
$$

then we will see that a consoidal field and a toroidal field is ***orthogonal*** on the sphere (in the sense of inner products, but not physically perpendicular to each other at each point)

$$
\langle \mathbf{A}_c, \mathbf{A}_T \rangle_S = \langle \nabla_s g\cdot \Lambda_s h \rangle_S = \langle \nabla_s\cdot (g\Lambda_sh) \rangle_S = 0.
$$

It follows that any vector field on a sphere (or in a shell, since the solution exists on each sphere) into three components: radial, consoidal and toroidal, described by three scalars

$$
\mathbf{A} = A_r \hat{\mathbf{r}} + \nabla_s g + \Lambda_s h = A_r \hat{\mathbf{r}} + \nabla_s g + \nabla_s\times h\hat{\mathbf{r}}.
$$

and such decomposition is unique given zero-averaging constraints. The scalars $$A_r$$, $$g$$ and $$h$$ are termed (primary) Helmholtz scalars; $$g$$ and $$h$$ are also termed consoidal and toroidal scalars.

The divergence of a vector field with Helmholtz representation

$$
\begin{aligned}
\nabla\cdot \mathbf{A} &= \nabla\cdot (A_r \hat{\mathbf{r}} + \nabla_s g + \nabla\times h\mathbf{r}) = (r^{-1}\nabla_s + \hat{\mathbf{r}}\partial_r)\cdot (A_r \hat{\mathbf{r}} + \nabla_s g) \\
&= 2r^{-1}A_r + r^{-1}\nabla_s^2 g + \partial_r A_r = \partial_r A_r + 2r^{-1} A_r + r^{-1}\nabla_s \cdot \mathbf{A}_s.
\end{aligned}
$$

and the curl of a vector field

$$
\begin{aligned}
\nabla\times \mathbf{A} &= \nabla\times A_r\hat{\mathbf{r}} + \nabla\times \nabla_s g + \nabla\times \Lambda_s h \\
&= (r^{-1} \nabla_s + \partial_r \hat{\mathbf{r}})\times A_r \hat{\mathbf{r}} + \nabla\times (r\nabla - \mathbf{r}\partial_r)g + (r^{-1}\nabla_s + \hat{\mathbf{r}}\partial_r)\times \Lambda_sh \\
&= -r^{-1}\Lambda_s A_r + \nabla r\times \nabla g- \nabla\times (\partial_r g \, \mathbf{r}) + r^{-1} \nabla_s\times \Lambda_s h + \hat{\mathbf{r}}\times \Lambda_s(\partial_r h) \\
&= -\Lambda_s(r^{-1} A_r) - r^{-1} \nabla\times (g\mathbf{r}) - \nabla\times (\partial_r g \mathbf{r}) + r^{-1}(\hat{\mathbf{r}}\nabla_s^2 - \nabla_s)h - \nabla_s(\partial_r h) \\
&= \Lambda_s\left(r^{-1}\partial_r(rg) - r^{-1}A_r\right) + (\nabla_s^2(r^{-1}h))\hat{\mathbf{r}} - \nabla_s(r^{-1}\partial_r(rh)).
\end{aligned}
$$

Therefore imposing the zero-averaging condition, the curl of a vector has the representation

$$
\nabla\times \mathbf{A} = \tilde{f}\,\hat{\mathbf{r}} + \nabla_s \tilde{g} + \Lambda_s \tilde{h},\qquad \tilde{f} = \nabla_s^2\frac{h}{r},\quad \tilde{g} = - \frac{1}{r}\frac{\partial(rh)}{\partial r},\quad \tilde{h} = \frac{1}{r}\left[\frac{\partial(rg)}{\partial r} - A_r + \langle A_r\rangle_S \right].
$$

### Equivalent representation
In the region where sufficiently smooth vector fields have the Helmholtz representation, that is, can be decomposed into radial, consoidal and toroidal parts

$$
\mathbf{A} = A_r \hat{\mathbf{r}} + \nabla_sg + \Lambda_s h
$$

it can be shown that any sufficiently smooth vector field has the representation

$$
\mathbf{v} = \nabla S - \nabla\times T\mathbf{r} - \nabla\times \nabla\times P\mathbf{r}.
$$

This is a consequence of existence of Helmholtz decomposition

$$
\mathbf{v} = \nabla V + \nabla\times \mathbf{A}
$$

and if $$\mathbf{A}$$ is further written in Helmholtz representation, this yields

$$
\begin{aligned}
\mathbf{v} &= \nabla V + \nabla\times A_r \hat{\mathbf{r}} + \nabla\times \nabla_s g + \nabla\times \Lambda_s h \\
&= \nabla V + \nabla\times (r^{-1}A_r) \mathbf{r} - \nabla\times \nabla \times h\mathbf{r} - \nabla\times (r^{-1}\partial_r(rg)\mathbf{r}) \\
&= \nabla V + \nabla\times (r^{-1}(A_r - \partial_r (rg) - \langle A_r\rangle_S)\mathbf{r}) - \nabla\times \nabla\times h\mathbf{r} \\
&= \nabla S - \nabla \times T\mathbf{r} - \nabla\times \nabla \times P\mathbf{r}
\end{aligned}
$$

where

$$
S = V, \quad T = \tilde{h} = \frac{1}{r}\left[\frac{\partial (rg)}{\partial r} - A_r + \langle A_r \rangle_S\right],\quad P = h.
$$

### Vector spherical harmonics
Helmholtz representation of vectors, combined with spherical harmonic of the Helmholtz scalars, gives rise to the so-called vector spherical harmonics (Backus 1986, Dahlen and Tromp 1999). These can be used as a basis for representing vectors (Sabaka et al., 2010). For instance, if the scalars are expanded using SH,

$$
f = \sum_{n=0}^\infty \sum_{m=-n}^n f_n^m(r)\, Y_n^m(\theta, \phi)
$$

where for the complex formulation

$$
Y_n^m(\theta, \phi) = P_n^m(\cos\theta)e^{i m\phi}
$$

and for the real formulation

$$
Y_n^m(\theta, \phi) = P_n^m(\cos\theta) \cos\phi,\quad Y_n^{-m}(\theta, \phi) = P_n^{|m|}(\cos\theta) \sin\phi, \quad m>0.
$$

For Helmholtz representation, its primary scalar $$\langle g\rangle = \langle h \rangle = 0$$, hence $$g_0 = h_0 = 0$$, and the series starts from $$n=1$$. Therefore the vector field has the expansion

$$
\mathbf{A} = \sum_{n,m} f_n^m(r) \, Y_n^m(\theta,\phi)\hat{\mathbf{r}} + \sum_{n,m}g_n^m(r) \, \nabla_s Y_n^m(\theta,\phi) + \sum_{n,m} h_n^m(r) \, \Lambda_s Y_n^m(\theta,\phi).
$$

where we used the fact that $$\nabla_s$$ and $$\Lambda_s$$ commute with functions of $$r$$. This form yields three sets of **vector spherical harmonics**

$$
\begin{aligned}
\mathbf{P}_n^m(\theta,\phi) &= Y_n^m(\theta,\phi) \hat{\mathbf{r}} \\
\mathbf{B}_n^m(\theta,\phi) &= \nabla_s Y_n^m(\theta,\phi) \\
\mathbf{C}_n^m(\theta,\phi) &= -\Lambda_s Y_n^m(\theta,\phi) = -\hat{\mathbf{r}}\times \mathbf{B}_n^m(\theta,\phi) = \nabla\times Y_n^m(\theta, \phi)\mathbf{r}.
\end{aligned}
$$

The name as well as the notations seems to be introduced by Dahlen and Tromp (1999), but the letters do not seem to have specific meanings (for instance, how is the first one 'P'? it is definitely not all of poloidal field; why is the last one 'C'? If anything should have the notation 'C', it should be 'B', since 'B' is consoidal).
These vector basis have the property of being mutually orthogonal on the surface, i.e. 

$$
\langle \mathbf{K}_n^m, \mathbf{L}_l^k\rangle \equiv 0,\, (\mathbf{K}\neq \mathbf{L}),\quad \langle \mathbf{K}_n^m(\theta,\phi), \mathbf{K}_l^k(\theta,\phi)\rangle = \langle \mathbf{K}_n^m,\mathbf{K}_n^m\rangle \delta_{nl} \delta_{mk}.
$$

That is, vector spherical harmonics are orthogonal between different families, and are also orthogonal between different order-degree configurations within the same type. The former orthogonality is mostly natural consequence from the aforementioned properties. First,

$$
\mathbf{P}_n^m\cdot \mathbf{B}_n^m=0,\quad \mathbf{P}_n^m\cdot \mathbf{C}_n^m = 0
$$

because $$\mathbf{P}_n^m$$ is radial, but $$\mathbf{B}_n^m$$ and $$\mathbf{C}_n^m$$ are both surface tangent fields, they are physically perpendicular in the space, and their inner products naturally vanish. Next,

$$
\langle\mathbf{B}_n^m,\mathbf{C}_l^k \rangle = \langle\nabla_s Y_n^m\cdot \Lambda_s Y_l^k \rangle_S = \langle\nabla_s\cdot (Y_n^m\Lambda_s Y_l^k)\rangle_S = 0.
$$

Therefore, the different families are orthogonal. The orthogonality within the families come from both surface operator properties and properties of SH. For $$\mathbf{P}_n^m$$ it is straightforwardly

$$
\langle \mathbf{P}_n^m,\mathbf{P}_l^k\rangle_S = \langle Y_n^m,Y_l^k \rangle_S = \langle Y_n^m, Y_n^m\rangle_S\, \delta_{nl}\delta_{mk}
$$

and inherits orthogonality from SH. Similarly,

$$
\begin{aligned}
\langle \mathbf{B}_n^m, \mathbf{B}_l^k \rangle_S &= \langle \nabla_s Y_n^m, \nabla_s Y_l^k \rangle = \langle\nabla_s\cdot (Y_n^m \nabla_s Y_l^k)\rangle - \langle Y_n^m \nabla_s^2 Y_l^k \rangle = l(l+1)\langle Y_n^m, Y_l^k\rangle \\
\langle \mathbf{C}_n^m, \mathbf{C}_l^k \rangle_S &= \langle \Lambda_s Y_n^m, \Lambda_s Y_l^k \rangle = \langle\Lambda_s\cdot (Y_n^m \Lambda_s Y_l^k)\rangle - \langle Y_n^m \nabla_s^2 Y_l^k \rangle = l(l+1)\langle Y_n^m, Y_l^k\rangle
\end{aligned}
$$

therefore are all orthogonal within the group.

---
## Mie representation for solenoidal fields

### Toroidal and Poloidal fields
We have already introduced the term toroidal field; it has alternative expressions

$$
\mathbf{A}_T = \Lambda_sT = -\nabla_s\times T\hat{\mathbf{r}} = -\nabla\times T \mathbf{r} = \mathbf{r}\times \nabla T = \hat{\mathbf{r}}\times \nabla_s T.
$$

From these expressions we conclude immediately that
- A toroidal field is solenoidal (since it is the curl of a vector field);
- A toroidal field is tangent to the sphere (since it is the cross product between $$\mathbf{r}$$ and a vector)
- If $$T$$ is analytic / N times continuously differentiable at $$\mathbf{r}=0$$, $$\mathbf{A}_T$$ will be analytic / (N-1) times continuously differentiable.
- $$\Lambda_s T$$ itself is nothing but the Helmholtz representation of the toroidal field. The primary toroidal scalar is $$T - \langle T\rangle_S$$.
From a toroidal field we can introduce a new field:

$$
\begin{aligned}
\mathbf{A}_P &= \nabla\times \Lambda_s P = \nabla\times (\mathbf{r}\times \nabla P) = -\nabla\times (\nabla \times P \mathbf{r}) \\
&= \mathbf{r}\nabla^2 P - \nabla \left(\frac{\partial}{\partial r}(rP)\right) \\
&= \hat{\mathbf{r}} \nabla_s^2 \frac{P}{r} - \nabla_s\left(\frac{1}{r}\frac{\partial}{\partial r}(rP)\right).
\end{aligned}
$$

From the definition and these expressions we conclude immediately that
- A poloidal field is also solenoidal. 
- The tangent component of a poloidal field is consoidal/irrotational.
- If $$P$$ is analytic / N times continuously differentiable at $$\mathbf{r}=0$$, $$\mathbf{A}_P$$ will be analytic / (N-2) times continuously differentiable.
- The last line above is actually the Helmholtz representation of a poloidal field. The primary poloidal scalar is $$r^{-1}\partial_r(r(P - \langle P\rangle_S))$$ (since surface averaging commutes with $$r$$ and $$\partial_r$$).
Based on these properties, a toroidal field and a poloidal field is always *orthogonal* on a sphere

$$
\langle \mathbf{A}_T, \mathbf{A}_P\rangle_S = \left\langle \Lambda_s T, \hat{\mathbf{r}}V_1\right\rangle_S - \left\langle \Lambda_s T, \nabla_s V_2\right\rangle_S = \langle 0\rangle_S - \langle \nabla_s\cdot (V_2 \Lambda_s T)\rangle_S \equiv 0.
$$

Both toroidal and poloidal scalars can be determined up to a function of $$r$$. **If we again require zero surface-average, then the scalars are uniquely determined, and vanishes at the origin.**
One important aspect of toroidal and poloidal vector fields is that the curl operator converts one to another. Indeed by definition the curl of a toroidal field

$$
\nabla\times \Lambda_sT = \nabla\times (\mathbf{r}\times \nabla T) = -\nabla\times \nabla \times T\mathbf{r}
$$

is a poloidal field. On the other hand, using the second expression for $$\mathbf{P}$$, the curl of a poloidal field

$$
\nabla\times (\nabla\times \Lambda_sP) = \nabla\times (\mathbf{r}\nabla^2 P - \nabla(\partial_r(rP))) = -\mathbf{r}\times \nabla(\nabla^2 P) = -\Lambda_s (\nabla^2 P)
$$

is a toroidal field. This inspires yet another identity that $$\Lambda_s$$ commutes with the Laplacian

$$
\nabla\times \nabla\times \Lambda_s P = \nabla(\nabla\cdot \Lambda_sP) - \nabla^2(\Lambda_s P) = - \nabla^2 (\Lambda_s P) \quad \Longrightarrow\quad \nabla^2 \Lambda_s = \Lambda_s \nabla^2.
$$

Furthermore, this expression converts one primary scalar to the other

$$
\langle P \rangle_S=0, \,\forall r \quad \Longrightarrow\quad \langle \nabla^2P\rangle_S = \frac{1}{r^2}\frac{dr}{dr}r^2\langle P\rangle_S = 0.
$$

### Mie representation
Any **solenoidal** vector field (divergence free, $$\nabla\cdot \mathbf{A} = 0$$) can be decomposed into a toroidal field and a poloidal field:

$$
\mathbf{A} = \mathbf{A}_T + \mathbf{A}_P = \Lambda_s T + \nabla\times \Lambda_s P = -\nabla\times T\mathbf{r} - \nabla\times \nabla\times P \mathbf{r}.
$$

This **toroidal-poloidal decomposition** is also termed **Mia representation**. This states a solenoidal field has two independent variables (since zero divergence already gives a constraint, reducing three components to two independent ones). Under zero averaging condition, $$T$$ and $$P$$ are unique.

There are apparently multiple approaches to prove such a representation exists for solenoidal fields. For instance, [Sabaka et al., 2010](https://doi.org/10.1007/978-3-642-01546-5_17) provide a proof where Mie representation is a natural consequence for solenoidal fields in the region where vectors can be expressed in the equivalence of Helmholtz representation

$$
\mathbf{v} = \nabla S - \nabla\times T\mathbf{r} - \nabla\times \nabla \times P\mathbf{r}.
$$

To see how that is the case, we only need to show that the potential term can be absorbed into the poloidal field. When the field is solenoidal, potential function $$S$$ is harmonic:

$$
\nabla\cdot \mathbf{v} = \nabla\cdot \nabla S + 0 + 0 = \nabla^2 S = 0.
$$

Note that the poloidal field has the explicit expression

$$
\nabla\times \nabla\times P\mathbf{r} = \nabla \frac{\partial}{\partial r}(rP) - \mathbf{r}\nabla^2 P
$$

therefore a potential field can be absorbed into the first term. In this case we can define an additional poloidal potential

$$
P_s = -\frac{1}{r}\int S \, dr,\quad S = -\frac{\partial}{\partial r}(rP_s)
$$

We can verify $$P_s$$ defined as such is also harmonic

$$
\begin{aligned}
\nabla^2 P_s &= -\frac{1}{r^2} \partial_r \left[r^2 \partial_r \left(\frac{1}{r} \int S \,dr\right)\right] + \frac{1}{r^2} \nabla_s^2 P_s\\
&= -\frac{1}{r^2} \partial_r \left[r^2 \left(-\frac{1}{r^2} \int S \,dr + \frac{S}{r} \right)\right] - \frac{1}{r^3}\int \nabla_s^2 S\, dr\\
&= -\frac{1}{r} \partial_r S - \frac{1}{r^3}\int \nabla_s^2 S\, dr = -\frac{1}{r^3} r^2 \partial_r S - \frac{1}{r^3}\int \nabla_s^2 S\, dr \\
&= -\frac{1}{r^3} \int\partial_r(r^2 \partial_r S) \, dr - \frac{1}{r^3}\int \nabla_s^2 S\, dr \\
&= -\frac{1}{r^3}\int r^2 \nabla^2 S \, dr = 0.
\end{aligned}
$$

Therefore the potential field can be completely absorbed into the poloidal field.

$$
-\nabla\times \nabla \times (P + P_s) \mathbf{r} = -\nabla\times \nabla\times P\mathbf{r} + \nabla S.
$$

and Mie representation exists. $$\blacksquare$$

Another approach by [Backus, 1986](https://doi.org/10.1029/RG024i001p00075) is more straightforward, and directly constructs the scalars from Helmholtz representations. First, any vector field in a shell has Helmholtz representation

$$
\mathbf{A} = A_r \hat{\mathbf{r}} + \nabla_s g + \Lambda_s h
$$

where $$\langle g\rangle_S = \langle h \rangle_S = 0$$. On the other hand, compare it with the superposition of a toroidal and a poloidal field

$$
\mathbf{T} + \mathbf{P} = \hat{\mathbf{r}} \nabla_s^2 \left(\frac{P}{r}\right) - \nabla_s\left(\frac{1}{r}\frac{\partial}{\partial r}(rP)\right) + \Lambda_s T
$$

We can assign $$T=h$$. Next, we can solve for $$P$$ which satisfies

$$
\nabla_s^2 P = rA_r,\quad \langle P\rangle_S = 0.
$$

The solution to this equation exists (see [[#Surface Laplacian]]). Finally, for a solenoidal field

$$
\nabla\cdot \mathbf{A} = \frac{1}{r^2}\partial_r(r^2A_r) + \nabla\cdot \nabla_s g = \frac{1}{r^2}\partial_r(r^2A_r) + \frac{1}{r} \nabla_s^2 g=0
$$

hence the field $$g$$ is given by the surface Poisson equation

$$
\nabla_s^2g=-\frac{1}{r}\frac{\partial}{\partial r}(r^2 A_r) = -\frac{1}{r}\frac{\partial}{\partial r}(r \nabla_s^2 P) = -\nabla_s^2\left[\frac{1}{r}\frac{\partial}{\partial r}(r P)\right],\quad \langle g\rangle_S = 0.
$$

We immediately realize that due to uniqueness of the solution fulfilling these two conditions,

$$
g = -\frac{1}{r}\frac{\partial}{\partial r}(rP)
$$

is the unique solution to the aforementioned problem. Therefore the solenoidal field

$$
\mathbf{A} = \mathbf{T} + \mathbf{P} = \hat{\mathbf{r}} \nabla_s^2 \left(\frac{P}{r}\right) - \nabla_s\left(\frac{1}{r}\frac{\partial}{\partial r}(rP)\right) + \Lambda_s T = \nabla\times \Lambda_s P + \Lambda_sT = -\nabla\times \nabla\times P\mathbf{r} - \nabla\times T\mathbf{r}.
$$

and Mie representation is constructed. $$\blacksquare$$ 

*Remark*: It is merely a convention whether the toroidal field is expressed as $$\Lambda_s h$$ or $$-\Lambda_s h$$. Backus apparently develops his paper on the former, so that there is no sign discrepancy between his Helmholtz and Mie representations (see the signs in [[#Equivalent representation]]). In addition, $$\Lambda_s$$ defined in this way is the actual surface curl. Dahlen and Tromp, Sabaka et al. and many other literatures use the latter, so that the curl and the double curl terms have positive signs. Except for a negative sign for any equations with a odd number of $$\Lambda_s$$, all equations hold exactly the same.

It is important to see that solenoidal field has three equivalent forms

$$
\mathbf{A} = \Lambda_s T + \nabla\times \Lambda_s P = -\nabla\times\nabla\times P\mathbf{r} - \nabla\times T\mathbf{r} = \hat{\mathbf{r}}\left(\frac{1}{r}\nabla_s^2 P\right) - \nabla_s\left(\frac{1}{r}\frac{\partial (rP)}{\partial r}\right) + \Lambda_s T
$$

The first is the definition; the second is another form of Mie representation, which allows manipulation using 3-D differential operators; and the last is the Helmholtz representation equivalent, which allows manipulation using pure surface operators.
Using the last relation, we have

$$
\mathbf{r}\cdot \mathbf{A} = \nabla_s^2 P,\quad \mathbf{r}\cdot \nabla\times \mathbf{A} = \Lambda_s\cdot \mathbf{A} = \Lambda_s\cdot \Lambda_s T = \nabla_s^2 T. 
$$


---

## Applications

### Vector SH representation of toroidal and poloidal fields
Toroidal and poloidal scalars can be expanded using SH

$$
T = \sum_{n=1}^\infty \sum_{m=-n}^n T_n^m(r)\, Y_n^m(\theta,\phi),\quad P = \sum_{n=1}^\infty \sum_{m=-n}^n P_n^m(r)\, Y_n^m(\theta,\phi)
$$

where the lower degree $$n=1$$ comes from the zero-averaging condition. Plugging in the Helmholtz representation of the toroidal and poloidal fields, we find the fields can be expanded using the exact same radial functions with vector SH basis

$$
\begin{aligned}
\mathbf{A}_T &= \sum_{n,m} T_n^m(r) \, \hat{\mathbf{r}}\times \nabla_s Y_n^m(\theta,\phi) = -\sum_{n,m} T_n^m(r)\, \mathbf{C}_n^m(\theta,\phi) \\
\mathbf{A}_P &= \sum_{n,m} r^{-1} P_n^m(r) \, [\hat{\mathbf{r}}\nabla_s^2 Y_n^m(\theta,\phi)] - \sum_{n,m} r^{-1}\partial_r(rP_n^m(r))\, \nabla_s Y_n^m(\theta,\phi) \\
&= -\sum_{n,m} n(n+1) r^{-1} P_n^m(r) \, \mathbf{P}_n^m(\theta,\phi) - \sum_{n,m}r^{-1}\partial_r(rP_n^m(r)) \,\mathbf{B}_n^m(\theta,\phi).
\end{aligned}
$$

Now the orthogonality between toroidal and poloidal field can also be derived based on the orthogonality of the vector SH basis.

### Equating Gauss and Mie representations
An important use of Mie representation in geomagnetism is representation of magnetic field where the electrical current may or may not be present. Since $$\nabla\cdot \mathbf{B} = 0$$ always holds true, we can always produce the Mie representation of magnetic field

$$
\begin{aligned}
\mathbf{B} &= \Lambda_s  T + \nabla\times \Lambda_s P \\
&= \hat{\mathbf{r}}\nabla_s^2 \left(\frac{P}{r}\right) - \nabla_s\left(\frac{1}{r}\frac{\partial (rP)}{\partial r}\right) + \Lambda_s T.
\end{aligned}
$$

The second line gives the corresponding Helmholtz representation. For a solenoidal field that is also irrotational, we have the constraints on $$T$$ and $$P$$:

$$
\nabla\times \mathbf{B} = -\Lambda_s \nabla^2 P + \nabla\times \Lambda_s T=\mathbf{0}\quad \Longrightarrow \quad \nabla^2 P=0, \quad T=0.
$$

Meaning an irrotational field can only be poloidal.
On the other hand, in current-free regions, Gauss representation is a simpler representation because it contains only one scalar. For any irrotational vector field, Gauss representation gives

$$
\mathbf{B} = -\nabla V = -\hat{\mathbf{r}}\frac{\partial V}{\partial r} - \nabla_s \frac{V - \langle V\rangle_S}{r}.
$$

The second equation is the corresponding Helmholtz representation. The extra $$\langle V \rangle_S$$ term is introduced to impose zero-average, but leaves the field completely unchanged. For a field that is both irrotational and solenoidal, there is additional constraint

$$
\nabla^2 V = 0,\quad \langle \partial_r V \rangle_S = \partial_r \langle V\rangle_S = 0\quad \Longrightarrow\quad \langle V\rangle_S =cst.
$$

and hence such $$V$$ can be found which has zero average on every sphere.

Consider magnetic field in source-free regions, the field is both solenoidal and irrotational, in which case we can equate the Helmholtz scalars

$$
\nabla_s^2 P = -r \frac{\partial V}{\partial r},\quad V = \frac{\partial (rP)}{\partial r}.
$$

When one of them (which satisfies zero-surface-average) is given, the other one can be calculated

$$
V(\mathbf{r}) = -\int \frac{\nabla_s^2 P}{r}dr,\quad P(\mathbf{r})=\frac{1}{r}\int V\, dr.
$$

For instance, in source-free region, in a spherical shell, the potential in Gauss representation can be expanded into spherical harmonics from degree $$1$$,

$$
V(\mathbf{r}) = a\sum_{n=1}^\infty \sum_{m=-n}^n \left[\varepsilon_n^m \left(\frac{r}{a}\right)^n + \iota_n^m\left(\frac{r}{a}\right)^{-(n+1)}\right] Y_n^m(\theta,\phi)
$$

the corresponding poloidal scalar can be integrated from this to be

$$
P(\mathbf{r}) = a\sum_{n=1}^\infty \sum_{m={-n}}^n\left[\frac{\varepsilon_n^m}{n + 1}\left(\frac{r}{a}\right)^{n}-\frac{\iota_n^m}{n}\left(\frac{r}{a}\right)^{-(n+1)}\right]Y_n^m(\theta,\phi).
$$

### Incompressible flow of rotating fluid
Consider the Navier Stokes equation for incompressible flow, where the fluid is Newtonian and its properties (viscosity, density) homogeneous in the domain. In the rotating frame, the Navier-Stokes equation has the form

$$
\frac{\partial \mathbf{u}}{\partial t} + \mathbf{u}\cdot \nabla \mathbf{u} + 2\Omega \hat{\mathbf{z}}\times \mathbf{u} = -\nabla p + \nu\nabla^2 \mathbf{u} + \mathbf{f}.
$$

Since now the velocity field is solenoidal, it has the toroidal-poloidal representation

$$\mathbf{u} = \Lambda_s T + \nabla\times \Lambda_s P = -\nabla\times T\mathbf{r} - \nabla\times \nabla\times P\mathbf{r}. $$

Plugging in the momentum equation

$$
\left(\frac{\partial}{\partial t} -\nu \nabla^2 + 2\Omega\hat{\mathbf{z}}\times \right) \left(\Lambda_s T + \nabla\times \Lambda_s P\right) = -\mathbf{u}\cdot \nabla \mathbf{u} - \nabla p + \mathbf{f}.
$$

Note there are several commutation properties. First, the temporal differentiation commutes with all spatial differentations, including the surface operators. Second, the Laplacian $$\nabla^2$$ commutes with operator $$\Lambda_s$$. We can further show it commutes also with $$\nabla\times \Lambda_s$$:

$$
\begin{aligned}
\nabla^2(\nabla\times \Lambda_s P) &= \nabla(\nabla\cdot \nabla\times \Lambda_s P) - \nabla\times \nabla\times\nabla\times \Lambda_s P \\
&= 0 - \nabla\times (\nabla(\nabla\cdot \Lambda_s P) - \nabla^2 \Lambda_s P) \\
&= - 0 + \nabla\times \Lambda_s \nabla^2 P = \nabla\times \Lambda_s\nabla^2 P.
\end{aligned}
$$

where we used the property $$\nabla\cdot (\nabla\times \mathbf{A})\equiv 0$$, $$\nabla\cdot \Lambda_s\equiv 0$$, etc. Therefore, the surface operators can be moved to the front for the leading two terms, and the equation writes

$$
\Lambda_s\left(\frac{\partial}{\partial t} - \nu\nabla^2\right) T +  \nabla\times \Lambda_s \left(\frac{\partial}{\partial t} - \nu\nabla^2\right) P + 2\Omega \hat{\mathbf{z}}\times \mathbf{u} = -\mathbf{u}\cdot \nabla \mathbf{u} - \nabla p + \mathbf{f}.
$$

We note the following three relations

$$
\begin{aligned}
\Lambda_s\cdot \Lambda_s h &= \mathbf{r}\cdot \nabla\times \Lambda_s h = \nabla_s^2h \\
\Lambda_s\cdot (\nabla\times \Lambda_s h) &= \mathbf{r}\cdot \nabla\times (\nabla\times \Lambda_s h) = \Lambda_s\cdot (\mathbf{r}\nabla^2 h - \nabla(\partial_r (rP))) = 0\\
\Lambda_s\cdot (\nabla\times \nabla\times \Lambda_s h) &= \mathbf{r}\cdot \nabla\times \nabla\times \nabla\times \Lambda_s h = \Lambda_s\cdot (\nabla(\nabla\cdot \Lambda_s h) - \nabla^2 \Lambda_s h) \\
&=\Lambda_s\cdot (0 - \nabla^2\Lambda_s h) = - \Lambda_s\cdot \nabla^2 \Lambda_s h = - \nabla^2\Lambda_s\cdot \Lambda_s h = -\nabla^2\nabla_s^2 h.
\end{aligned}
$$

From the first and the second properties we see that taking the surface divergence of a toroidal-poloidal field gives $$\nabla_s^2$$ of the toroidal scalar; from the second and the third relations, $$\Lambda_s\cdot \nabla\times$$ operating on the same field yields $$-\nabla^2 \nabla_s^2$$ of the poloidal scalar. Hence we have

$$
\begin{aligned}
\Lambda_s\cdot (\sim):\quad \nabla_s^2\left(\frac{\partial}{\partial t} - \nu\nabla^2\right) T + 2\Omega \Lambda_s\cdot (\hat{\mathbf{z}}\times \mathbf{u}) &= -\Lambda_s \cdot (\mathbf{u}\cdot \nabla\mathbf{u}) + \Lambda_s\cdot \mathbf{f} \\
\Lambda_s\cdot\nabla\times (\sim):\quad -\nabla^2 \nabla_s^2 \left(\frac{\partial}{\partial t} - \nu\nabla^2\right) P + 2\Omega\Lambda_s\cdot \nabla\times (\hat{\mathbf{z}}\times \mathbf{u}) &= -\Lambda_s\cdot \nabla\times (\mathbf{u}\cdot \nabla \mathbf{u}) + \Lambda_s\cdot \nabla\times \mathbf{f}
\end{aligned}
$$

where the operators $$\nabla^2$$ and $$\nabla_s^2$$ also both commute with the operators in the brackets, and can freely move inwards if desired. The potential field (pressure gradient) does not manifest whatsoever under these operations. The nonlinear term aside, it would seem that the origional equation disintegrate into two decoupled scalars equations of $$T$$ and $$P$$. However, **the Coriolis force introduces coupling between the toroidal and the poloidal components.** First, we write down two frequently used vector identities

$$
\nabla\times (\hat{\mathbf{z}}\times \mathbf{u}) = -\hat{\mathbf{z}}\cdot \nabla \mathbf{u},\qquad \mathbf{A}\times \nabla\times \mathbf{B} = \nabla \mathbf{B} \cdot \mathbf{A} - \mathbf{A}\cdot \nabla \mathbf{B},\quad \nabla(\mathbf{A}\cdot \mathbf{B}) = \nabla\mathbf{A}\cdot \mathbf{B} + \nabla \mathbf{B}\cdot \mathbf{A}
$$

hence the Coriolis terms are symmetric in two equations

$$
2\Omega\Lambda_s \cdot \nabla\times (\hat{\mathbf{z}}\times \mathbf{u}) = -2\Omega\Lambda_s\cdot(\hat{\mathbf{z}}\cdot \nabla\mathbf{u}) = 2\Omega \Lambda_s \cdot (\hat{\mathbf{z}}\times (\nabla\times \mathbf{u})).
$$

This means the coupling term for $$P$$ takes the same form, except for swapping $$T$$ to $$-\nabla^2 P$$, and $$P$$ to $$T$$ in the $$\mathbf{u}$$ term. Plugging in the toroidal-poloidal representation, we have

$$
\begin{aligned}
2\Omega \Lambda_s \cdot (\hat{\mathbf{z}}\times \mathbf{u}) &= -2\Omega \mathbf{r}\cdot (\hat{\mathbf{z}}\cdot \nabla \mathbf{u}) = -2\Omega \hat{\mathbf{z}}\cdot \nabla \mathbf{u}\cdot \mathbf{r} = -2\Omega \hat{\mathbf{z}}\cdot \nabla \left(\Lambda_s T + \nabla\times \Lambda_s P\right)\cdot \mathbf{r} \\
&= -2\Omega \hat{\mathbf{z}}\cdot (\nabla(\mathbf{r}\cdot \Lambda_s T) - \nabla\mathbf{r}\cdot \Lambda_s T + \nabla(\mathbf{r}\cdot \nabla\times \Lambda_s P) - \nabla \mathbf{r}\cdot \nabla\times \Lambda_s P) \\
&= -2\Omega \hat{\mathbf{z}}\cdot (\mathbf{0} - \Lambda_s T + \nabla (\Lambda_s\cdot \Lambda_s P) - \nabla\times \Lambda_s P) \\
&= 2\Omega (\hat{\mathbf{z}}\cdot \Lambda_s)T - 2\Omega (\hat{\mathbf{z}}\cdot \nabla)\nabla_s^2 P + 2\Omega \hat{\mathbf{z}}\cdot (\mathbf{r}\nabla^2 P - \nabla\partial_r(rP))
\end{aligned}
$$

Note that $$\hat{\mathbf{z}} = \cos\theta \hat{\mathbf{r}} - \sin\theta \mathbf{e}_\theta$$, it has inner products $$\hat{\mathbf{z}}\cdot \Lambda_s = \partial_\phi$$, $$\hat{\mathbf{z}}\cdot \nabla = \cos\theta \partial_r - r^{-1}\sin\theta \partial_\theta$$, and $$\hat{\mathbf{z}}\cdot \mathbf{r} = r\cos\theta$$, hence

$$
\begin{aligned}
2\Omega \Lambda_s\cdot (\hat{\mathbf{z}}\times \mathbf{u}) &= 2\Omega \left[\frac{\partial T}{\partial \phi} - (\hat{\mathbf{z}}\cdot \nabla)\left(\nabla_s^2 P + \frac{\partial (rP)}{\partial r}\right) + r\cos\theta \nabla^2 P\right] \\
2\Omega \Lambda_s\cdot (\hat{\mathbf{z}}\times (\nabla\times \mathbf{u})) &= 2\Omega \left[-\frac{\partial \nabla^2 P}{\partial \phi} - (\hat{\mathbf{z}}\cdot \nabla)\left(\nabla_s^2 T + \frac{\partial (rT)}{\partial r}\right) + r\cos\theta \nabla^2 T\right].
\end{aligned}
$$

We can define the coupling operator

$$
\mathcal{Q} = \hat{\mathbf{z}}\cdot \nabla(\nabla_s^2 + \partial_rr^M) - r\cos\theta\nabla^2
$$

and the two scalar equations will be written as

$$
\begin{aligned}
\left(\frac{\partial}{\partial t} - \nu\nabla^2\right)\nabla_s^2 T + 2\Omega \frac{\partial T}{\partial \phi} - 2\Omega \mathcal{Q}P &= -\Lambda_s \cdot (\mathbf{u}\cdot \nabla\mathbf{u}) + \Lambda_s\cdot \mathbf{f} \\
-\left(\frac{\partial}{\partial t} - \nu\nabla^2\right) \nabla_s^2 \nabla^2  P - 2\Omega \frac{\partial \nabla^2 P}{\partial \phi} - 2\Omega\mathcal{Q}T &= -\Lambda_s\cdot \nabla\times (\mathbf{u}\cdot \nabla \mathbf{u}) + \Lambda_s\cdot \nabla\times \mathbf{f}
\end{aligned}
$$

The coupling operator have the alternative form ([Roberts, 1968](https://doi.org/10.1098/rsta.1968.0007)):

$$
\mathcal{Q}=\frac{\partial}{\partial z} + \frac{1}{2}\left(\nabla_s^2 \frac{\partial}{\partial z} + \frac{\partial}{\partial z} \nabla_s^2\right) = \hat{\mathbf{z}}\cdot \nabla + \frac{1}{2}\left(\nabla_s^2 (\hat{\mathbf{z}}\cdot \nabla) + (\hat{\mathbf{z}}\cdot \nabla) \nabla_s^2 \right).
$$

This can be derived using the Cartesian component form. Note that the coupling term gives rise to the poloidal part

$$
-\mathcal{Q}P = \Lambda_s \cdot (\hat{\mathbf{z}}\times \mathbf{u}_P) = - \mathbf{r}\cdot \nabla\times (\hat{\mathbf{z}}\times \nabla\times \nabla\times P\mathbf{r}) = \mathbf{r}\cdot (\hat{\mathbf{z}}\cdot \nabla)(\nabla(\partial_r(rP))-\mathbf{r}\nabla^2 P)
$$

where the last step uses the expression for $$-\nabla\times \nabla\times P\mathbf{r}$$ and the fact that when $$\mathbf{u}$$ is irrotational we have $$\nabla\times (\hat{\mathbf{z}}\times \mathbf{u}) = -(\hat{\mathbf{z}}\cdot \nabla)\mathbf{u}$$. The equation can be converted to Cartesian form (Einstein summation convention used)

$$
\mathcal{Q} = x_i \partial_z (x_i\nabla^2 - \partial_i - \partial_i x_j \partial_j )
$$

For this expression, we can either move $$\partial_z$$ to the front (outwards) or to the back (inwards), as long as certain commutation rules are observed. This gives

$$
\begin{aligned}
\mathcal{Q} &= (x_ix_i \nabla^2 \partial_z + z\nabla^2) - x_i\partial_i \partial_z - ((x_i\partial_i)(x_j \partial_j)\partial_z + x_i\partial_i\partial_z) \\
&= (r^2\nabla^2 - x_i\partial_i - (x_i\partial_i)(x_j\partial_j))\partial_z + z\nabla^2 - x_i\partial_i\partial_z \\
&= \nabla_s^2 \partial_z + z\nabla^2 - x_i\partial_i\partial_z\\
\mathcal{Q} &= (\partial_z(x_ix_i\nabla^2) - z\nabla^2) - (\partial_z(x_i\partial_i) - \partial_z) - (\partial_z(x_i\partial_i)(x_j\partial_j) - \partial_z(x_j\partial_j)) \\
&=\partial_z(r^2\nabla^2 - x_i\partial_i - (x_i\partial_i)(x_j\partial_j)) - z\nabla^2 + \partial_z + \partial_z(x_j\partial_j) \\
&= \partial_z \nabla_s^2 -z\nabla^2 + \partial_z + \partial_z(x_j\partial_j)
\end{aligned}
$$

If we sum the two expressions together

$$
\mathcal{Q} = \frac{1}{2} \left(\nabla_s^2\partial_z + \partial_z \nabla_s^2 + \partial_z + x_j\partial_j\partial_z + \partial_z - x_i \partial_i\partial_z\right) = \partial_z + \frac{1}{2}\left(\nabla_s^2\partial_z + \partial_z \nabla_s^2\right)
$$

which is exactly the Roberts 1968 expression. The expression can be shown to be equivalent to the spherical coordinate expression. It is easily seen from this formula that since $$\partial_z\nabla^2 = \nabla^2\partial_z$$, $$\mathcal{Q}$$ commutes with the Laplacian $$\nabla^2$$.


