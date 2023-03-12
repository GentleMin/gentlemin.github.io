---
layout: page
title: Curvilinear coordinates
description: Differential forms in curvilinear coordinates, using exterior differentials and Christoffel symbol.
importance: 1
date: 2023-02-02 12:00:00-0400
category: Maths
---

## Metric

Unless otherwise stated in this section, the superscript of a coordinate is interpreted as component or an index.
Coordinates in a frame with curvature are given by

$$
x_f^1=x_f^1(x^1, x^2, x^3), \quad x^2_f=x^2_f(x^1, x^2, x^3),\quad x_f^3=x_f^3(x^1, x^2, x^3)
$$

where $$x_f^i$$ are the new coordinates, and $$x^i$$ are Cartesian coordinates (coordinates in a curvature-free frame or flat space, i.e. Euclidean space). For an arbitrary coordinate frame, we can always express the infinitesimal line unit length as a quadratic form of the new coordinates

$$
ds^2 = \sum_{i,j} g_{ij} \, dx^i_f \, dx^j_f
$$

where the matrix $$(\mathbf{G})_{ij} = g_{ij}$$ is called the ***metric tensor***. If the metric is a diagonal matrix, then the corresponding coordinate frame is orthogonal curvilinear frame.

### Cartesian coordinates
The metric is given by

$$
ds^2 = dx^1 dx^1 + dx^2dx^2 + dx^3dx^3 = \sum_{i,j}\delta_{ij} \, dx^i \, dx^j, \quad
\mathbf{G} = \mathbf{I} = \begin{bmatrix} 
1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1
\end{bmatrix}
$$

### Cylindrical coordinates
The coordinates $$\rho, \phi, z$$ are given by 

$$
x^1 = \rho \cos\phi,\quad x^2 = \rho \sin\phi, \quad x^3 = z, \quad
\begin{bmatrix}
dx_1 \\ dx_2 \\ dx_3
\end{bmatrix} = 
\begin{bmatrix}
\cos\phi & -\rho \sin\phi & 0 \\ 
\sin\phi & \rho \cos\phi & 0 \\ 
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
d\rho \\ d\phi \\ dz
\end{bmatrix} = \mathbf{J}
\begin{bmatrix}
d\rho \\ d\phi \\ dz
\end{bmatrix}
$$

The line unit length is

$$
ds^2 = d\mathbf{x}^2 = \sum_{i,j} A_{im}A_{in} \, dx^m_c \, dx^n_c = 
\begin{bmatrix} d\rho \\ d\phi \\ dz \end{bmatrix}^T \mathbf{J}^T\mathbf{J} \begin{bmatrix} d\rho \\ d\phi \\ dz \end{bmatrix}.
$$

Therefore the metric is the diagonal matrix

$$
\mathbf{G} = \mathbf{J}^T \mathbf{J} = 
\begin{bmatrix}
1 & 0 & 0 \\ 0 & \rho^2 & 0 \\ 0 & 0 & 1
\end{bmatrix}.
$$

It can be seen in this example that the metric is tightly related to the Jacobi matrix $$\mathbf{J}$$ that links the curved space to the flat space. Whether the coordinate frame is orthogonal depends on whether the Jacobi matrix is orthogonal.

### Spherical coordinates
Similarly we have for spherical coordinates $$r, \theta, \phi$$

$$
x^1 = r\sin\theta \cos\phi, \quad x^2 = r\sin\theta \sin\phi, \quad x^3 = r\cos\theta
$$

The Jacobi matrix

$$
\mathbf{J} = \frac{\partial \mathbf{x}}{\partial \mathbf{x}_s} = \begin{bmatrix}
\sin\theta \cos\phi & r\cos\theta \cos\phi & -r\sin\theta \sin\phi \\ 
\sin\theta \sin\phi & r\cos\theta \sin\phi & r\sin\theta \cos\phi \\ 
\cos\theta & -r\sin\theta & 0
\end{bmatrix}
$$

Therefore the metric is the diagonal matrix

$$
\mathbf{G} = \mathbf{J}^T \mathbf{J} = 
\begin{bmatrix}
1 & 0 & 0 \\ 
0 & r^2 & 0 \\
0 & 0 & r^2 \sin\theta
\end{bmatrix}.
$$

---
## Exterior Differentiation

Define ***exterior differentiation*** as the linear operator on a scalar:

$$
d: f\mapsto df = \sum_i \frac{\partial f}{\partial x^i} \, dx^i.
$$

This gives the first exterior differentation. If apply the operator to another first exterior derivative form, we obtain the second exterior differentiation

$$
d\alpha = d\left(\sum_i \alpha_i dx^i \right) = \sum_{i,j} \frac{\partial \alpha_i}{\partial x^j} \, dx^i \wedge dx^j.
$$

Now the summation index is ordered, i.e. outer sum (the last summation) w.r.t. $$i$$, inner sum (the first summation) w.r.t. $$j$$. because the wedge product is ordered. The wedge product has the property

$$
dx^i\wedge dx^j = -dx^j \wedge dx^i\quad \Longrightarrow \quad dx^i \wedge dx^i = 0.
$$

Higher order wedge products has the property

$$
dx^{i_1} \wedge dx^{i_2} \cdots \wedge dx^{i_p} \cdots \wedge dx^{i_q} \cdots \wedge dx^{i_n} = -dx^{i_1} \wedge dx^{i_2} \cdots \wedge dx^{i_q} \cdots \wedge dx^{i_p} \cdots \wedge dx^{i_n}
$$

Therefore any permutation (transposition) changes the sign of the basis. As a corollary, an $$n$$-dimensional space can have up to $$n$$-th exterior derivative.

The ***hodge asterik*** (\*) is used to convert an element in its $$p$$-form ($$p$$-th exterior power) to its isomorphic $$(n-p)$$-form. That is to say

$$
*(dx^{i_1}\wedge dx^{i_2}\wedge \cdots dx^{i_p}) = \frac{\sqrt{|\mathbf{G}|}}{\prod_{k=1}^p g_{i_k i_k}} dx^{i_{p+1}} \wedge dx^{i_{p+2}} \wedge \cdots dx^{i_n}
$$

where $$(i_1, i_2 \cdots i_p, i_{p+1} \cdots i_n)$$ forms an even permutation. For instance, for 3-D cases, we have

$$
\begin{aligned}
*1 &= \sqrt{|\mathbf{G}|} \, dx^1 \wedge dx^2 \wedge dx^3 \\
*(dx^1) &= \frac{\sqrt{|\mathbf{G}|}}{g_{11}} \, dx^2\wedge dx^3 \\
*(dx^1\wedge dx^2) &= \frac{\sqrt{|\mathbf{G}|}}{g_{11} g_{22}} \, dx^3
\end{aligned}
$$

For orthgonal curvilinear coordinates we shall simply write $$g_i$$ instead of $$g_{ii}$$.

---
## Vector forms in curvilinear coordinates

Using these notations, we can efficiently derive the expressions for gradient of a scalar, curl of a vector, and divergence of a vector in arbitrary orthogonal curvilinear coordinates. These will be presented as special cases for exterior differentations.
First, note a tangential unit vector is expressed in its $$1$$-form as

$$\mathbf{e}_i = \sqrt{g_i} \, dx^i = h_i \, dx^i $$

where $$h_i=\sqrt{g_i}$$ is the square root of the diagonal element of the metric tensor.

The gradient of a scalar $$f(x^i)$$ is given by

$$
\begin{aligned}
\nabla f = df &= \sum_i \frac{\partial f}{\partial x^i} \, dx^i = \sum_i \frac{1}{h_i} \frac{\partial f}{\partial x^i} \mathbf{e}_i
\end{aligned}
$$

The curl of a vector $$\mathbf{A}(x^i)$$ (written in its $$1$$-form as $$A = \sum_i h_i A_i dx^i$$) is given by

$$
\begin{aligned}
\nabla \times \mathbf{A} = *dA &= *d\left(\sum_i h_i A_i \, dx^i\right) = *\left(\sum_{i, j} \frac{\partial (h_j A_j)}{\partial x^i} \, dx^i\wedge dx^j \right) \\ 
&= \sum_{i,j} \frac{\partial (h_j A_j)}{\partial x^i} \left(\frac{h_1 h_2 h_3}{h_i^2 h_j^2}\right) \sum_k \epsilon_{ijk} \, dx^k \\ 
&= \sum_{i,j} \frac{\partial (h_j A_j)}{\partial x^i} \left(\frac{h_1 h_2 h_3}{h_i^2 h_j^2 h_k}\right) \sum_k \epsilon_{ijk} \, \mathbf{e}_k \\
&= \sum_k \mathbf{e}_k \frac{h_k}{h_1 h_2 h_3} \sum_{i,j} \epsilon_{ijk} \, \frac{\partial (h_j A_j)}{\partial x^i}.
\end{aligned}
$$

The divergence of a vector $$\mathbf{A}(x^i)$$ is given by

$$
\begin{aligned}
\nabla\cdot \mathbf{A} = *d*A &= *d* \left(\sum_i h_i A_i \, dx^i \right) = *d\left(\sum_{i} h_iA_i \frac{h_1h_2h_3}{h_i^2} \, dx^j\wedge dx^k\right) \\ 
&= *\left(\sum_i \frac{\partial}{\partial x_i} \left(\frac{h_1h_2h_3}{h_i} A_i \right) \, dx^i\wedge dx^j \wedge dx^k \right) \\ 
&= \sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x_i} \left(\frac{h_1h_2h_3}{h_i} A_i \right)
\end{aligned}
$$

where the indices $$j,k$$ are chosen so that $$i,j,k$$ forms even permutation in the summation.
The Laplacian of a scalar $$f(x^i)$$ is given by

$$
\begin{aligned}
\nabla^2f = *d*df &= *d*\left(\sum_i \frac{\partial f}{\partial x^i} dx^i\right)\\
&= \sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x^i} \left(\frac{h_1h_2h_3}{h_i^2} \frac{\partial f}{\partial x^i}\right)
\end{aligned}
$$

where the second line uses 

$$
*d* \left(\sum_i a_i dx^i\right) = \sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x^i} \left(h_1h_2h_3 \frac{a_i}{h_i^2}\right)
$$

which is evident from the intermediate derivation of divergence formula.

Now we are ready to apply these formulae to common orthogonal curvilinear coordinates.

### Cartesian coordinates
The metric elements

$$h_1 = h_2=h_3=1.$$

Gradient of scalar

$$
\nabla f = \frac{\partial f}{\partial x^1} \mathbf{e}_1 + \frac{\partial f}{\partial x^2} \mathbf{e}_2 + \frac{\partial f}{\partial x^3} \mathbf{e}_3.
$$

Divergence of vector

$$
\nabla \cdot \mathbf{A} = \frac{\partial A_1}{\partial x^1} + \frac{\partial A_2}{\partial x^2} + \frac{\partial A_3}{\partial x^3}.
$$

Curl of vector

$$
\nabla\times \mathbf{A} = \left(\frac{\partial A_3}{\partial x^2} - \frac{\partial A_2}{\partial x^3}\right) \mathbf{e}_1 + \left(\frac{\partial A_1}{\partial x^3} - \frac{\partial A_3}{\partial x^1}\right) \mathbf{e}_2 + \left(\frac{\partial A_2}{\partial x^1} - \frac{\partial A_1}{\partial x^2}\right) \mathbf{e}_3.
$$

Laplacian of a scalar

$$
\nabla^2 f = \frac{\partial^2 A_1}{\partial x^1\partial x^1} + \frac{\partial^2 A_2}{\partial x^2\partial x^2} + \frac{\partial^2 A_3}{\partial x^3\partial x^3}.
$$

### Cylindrical coordinates
The indices are 1:$$\rho$$, 2:$$\phi$$, 3:$$z$$. The metric elements

$$
h_1 = 1,\quad h_2 = \rho, \quad h_3 = 1.
$$

Gradient of scalar

$$
\nabla f = \frac{\partial f}{\partial \rho} \mathbf{e}_\rho + \frac{1}{\rho} \frac{\partial f}{\partial \phi} \mathbf{e}_\phi +\frac{\partial f} {\partial z} \mathbf{e}_z.
$$

Divergence of vector

$$
\nabla \cdot \mathbf{A} = \frac{1}{\rho} \frac{\partial (\rho A_\rho)}{\partial \rho} + \frac{1}{\rho} \frac{\partial A_\phi}{\partial \phi} + \frac{\partial A_z}{\partial z}.
$$

Curl of a vector

$$
\nabla\times \mathbf{A} = \left(\frac{1}{\rho}\frac{\partial A_z}{\partial\phi} - \frac{\partial A_\phi}{\partial z}\right)\mathbf{e}_\rho + \left(\frac{\partial A_\rho}{\partial z} - \frac{\partial A_z}{\partial \rho}\right)\mathbf{e}_\phi + \left(\frac{1}{\rho} \frac{\partial(\rho A_\phi)}{\partial\rho} - \frac{1}{\rho} \frac{\partial A_\rho}{\partial \phi}\right)\mathbf{e}_z.
$$

Laplacian of a scalar

$$
\nabla^2 f = \frac{1}{\rho} \frac{\partial}{\partial \rho}\left(\rho \frac{\partial f}{\partial \rho}\right) + \frac{1}{\rho} \frac{\partial}{\partial \phi}\left(\frac{1}{\rho} \frac{\partial f}{\partial \phi}\right) + \frac{1}{\rho} \frac{\partial}{\partial z}\left(\rho \frac{\partial f}{\partial z}\right).
$$

### Spherical coordinates
The indices are 1:$$r$$, 2:$$\theta$$, 3:$$\phi$$. The metric elements

$$
h_1 = 1, \quad h_2 = r, \quad h_3 = r\sin\theta.
$$

Gradient of scalar

$$
\nabla f = \frac{\partial f}{\partial r} \mathbf{e}_r + \frac{1}{r} \frac{\partial f}{\partial \theta} \mathbf{e}_\theta + \frac{1}{r\sin\theta} \frac{\partial f} {\partial \phi} \mathbf{e}_\phi.
$$

Divergence of vector

$$
\nabla \cdot \mathbf{A} = \frac{1}{r^2} \frac{\partial (r^2 A_r)}{\partial r} + \frac{1}{r \sin\theta} \frac{\partial (\sin\theta A_\theta)}{\partial \theta} + \frac{1}{r\sin\theta} \frac{\partial A_\phi}{\partial \phi}.
$$

Curl of vector

$$
\begin{aligned}
\nabla\times \mathbf{A} =& \frac{1}{r\sin\theta}\left(\frac{\partial(\sin\theta A_\phi)}{\partial\theta} - \frac{\partial A_\theta}{\partial \phi}\right)\mathbf{e}_r \\
&+ \left(\frac{1}{r\sin\theta}\frac{\partial A_r}{\partial \phi} - \frac{1}{r}\frac{\partial (r A_\phi)}{\partial r}\right)\mathbf{e}_\theta \\
&+ \frac{1}{r} \left(\frac{\partial(r A_\theta)}{\partial r} - \frac{\partial A_r}{\partial \theta}\right)\mathbf{e}_\phi.
\end{aligned}
$$

Laplacian of scalar

$$
\nabla^2 f = \frac{1}{r^2} \frac{\partial}{\partial r}\left(r^2 \frac{\partial f}{\partial r}\right) + \frac{1}{r^2\sin\theta} \frac{\partial}{\partial \theta}\left(\sin\theta \frac{\partial f}{\partial \theta}\right) + \frac{1}{r^2 \sin^2\theta} \frac{\partial^2 f}{\partial \phi^2}.
$$

---
## Laplacian of a vector

It seems that exterior differentiation alone can only tackle the vector forms of differentiations. When a tensorial form whose rank is greater or equal to two is present, one would have to resort to other tools for formal derivation. Most commonly, deriving the gradient of a vector would require e.g. Christoffel symbols, see [Gradient of vector field using differential forms - Mathematics Stack Exchange](https://math.stackexchange.com/questions/2862079/gradient-of-vector-field-using-differential-forms).
Of course, formality aside, all of these expressions can be derived using vectors and dyadics, after deriving the derivative of unit vectors, i.e. $$\partial \mathbf{e}_i/ \partial x^j$$. Metric, exterior differentiation and Christoffel symbols are just formal tensorial expressions of these derivations that generalize to high dimensions and high orders.

A commonly used formulae, although containing higher-rank quantities in intermediate steps, can actually be derived using vector forms using vector identities. This is the Laplacian of a vector. The operator is formally

$$
\nabla^2 \mathbf{A} = \nabla\cdot \nabla \mathbf{A}.
$$

**This is not equivalent to taking the scalar Laplacian on each component of $$\mathbf{A}$$**, which is the case in Cartesian coordinates. The reason is again that in general curvilinear coordinates, the unit vectors are no longer invariant quantities. In other words, the dyadic $$\nabla \mathbf{A}$$ would have coupling terms between columns. Fortunately, it is possible to derive this expression without explicitly calculating $$\nabla \mathbf{A}$$. The trick is to use the identity

$$
\nabla^2 \mathbf{A} = \nabla(\nabla \cdot \mathbf{A}) - \nabla\times \nabla \times \mathbf{A}.
$$

Using the conclusions from above, this can be written as

$$
\begin{aligned}
\nabla^2 \mathbf{A} =& d(*d*A) - *d*dA \\
=& d \left(\sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x_i} \left(\frac{h_1h_2h_3}{h_i} A_i \right)\right) -*d\left(\sum_k \mathbf{e}_k \frac{h_k}{h_1 h_2 h_3} \sum_{i,j} \epsilon_{ijk} \, \frac{\partial (h_j A_j)}{\partial x^i} \right)\\
=& \sum_j dx^j \frac{\partial}{\partial x^j}\sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x_i} \left(\frac{h_1h_2h_3}{h_i} A_i \right) \\ 
&- \sum_l \mathbf{e}_l \frac{h_l}{h_1h_2h_3}\sum_{m,k}\epsilon_{mkl} \frac{\partial}{\partial x^m} \left(\frac{h_k^2}{h_1 h_2 h_3} \sum_{i,j} \epsilon_{ijk} \, \frac{\partial (h_j A_j)}{\partial x^i}\right) \\ 
=& \sum_l \bigg\{ \frac{1}{h_l} \frac{\partial}{\partial x^l} \sum_i \frac{1}{h_1h_2h_3} \frac{\partial}{\partial x_i} \left(\frac{h_1h_2h_3}{h_i} A_i \right) \\
&- \frac{h_l}{h_1h_2h_3} \sum_{m,k} \epsilon_{mkl} \frac{\partial}{\partial x^m} \left(\frac{h_k^2}{h_1 h_2 h_3} \sum_{i,j} \epsilon_{ijk} \, \frac{\partial (h_j A_j)}{\partial x^i}\right) \bigg\} \, \mathbf{e}_l.
\end{aligned}
$$

The rest is brute force calculation. Let us assume that given index $$i$$, the indices $$ijk$$ is the (unique) even permutation in 3-D; and the indices $$ikj$$ gives the (unique) odd permutation. Then each component of $$\nabla^2 \mathbf{A}$$ can be written as

$$
\begin{aligned}
(\nabla^2 \mathbf{A})_i &= \frac{1}{h_i} \partial_i \left(\frac{1}{h_ih_jh_k}\partial_i\left(\frac{h_ih_jh_k}{h_i} A_i\right)\right) \\
&+ \frac{h_i}{h_ih_jh_k} \left[\partial_j\left(\frac{h_k^2}{h_ih_jh_k} \partial_j (h_iA_i) \right) + \partial_k \left(\frac{h_j^2}{h_ih_jh_k}\partial_k(h_iA_i)\right)\right] \\ 
&+ \frac{1}{h_i} \partial_i \left(\frac{1}{h_ih_jh_k}\partial_j\left(\frac{h_ih_jh_k}{h_j} A_j\right)\right)
- \frac{h_i}{h_ih_jh_k} \partial_j\left(\frac{h_k^2}{h_ih_jh_k} \partial_i (h_jA_j) \right)\\
&+ \frac{1}{h_i} \partial_i \left(\frac{1}{h_ih_jh_k}\partial_k\left(\frac{h_ih_jh_k}{h_k} A_k\right)\right) - \frac{h_i}{h_ih_jh_k} \partial_k\left(\frac{h_j^2}{h_ih_jh_k} \partial_i (h_kA_k) \right)
\end{aligned}
$$

where the terms are arranged so the contributions of different components are grouped together. Since the latter four terms do not cancel out, the final solution for component $$i$$ contains contributions from $$j$$ and $$k$$.
A popular choice of writing this formula involves separating the terms that correspond to the scalar Laplacian, giving the form

$$
\begin{aligned}
(\nabla^2 \mathbf{A})_i &= \nabla^2 A_i \\
&+ \left[\frac{1}{h_i} \partial_i \left(\frac{1}{h_ih_jh_k} \partial_i \frac{h_ih_jh_k}{h_i}\right) + \frac{h_i}{h_ih_jh_k} \partial_j \left(\frac{h_k^2}{h_ih_jh_k} \partial_j h_i \right) + \frac{h_i}{h_ih_jh_k} \partial_k \left(\frac{h_j^2}{h_ih_jh_k} \partial_k h_i \right) \right] A_i \\ 
&+ \frac{2}{h_i h_j}\left(\partial_i A_j \, \partial_j \ln h_i - \partial_j A_j \, \partial_i \ln h_j\right) + \frac{A_j}{h_ih_j}\left(\partial_i\partial_j \ln\frac{h_ih_jh_k}{h_j^2} - 2 \partial_i \ln h_j\, \partial_j\ln h_k\right) \\
&+ \frac{2}{h_i h_k}\left(\partial_i A_k \, \partial_k \ln h_i - \partial_k A_k \, \partial_i \ln h_k\right) + \frac{A_k}{h_ih_k}\left(\partial_i\partial_k \ln\frac{h_ih_jh_k}{h_k^2} - 2 \partial_i \ln h_k\, \partial_k\ln h_j\right).
\end{aligned}
$$

One can verify this is correct. However, as seen below, for many curvilinear coordinate systems, it would be much simpler to plug in the metric and obtain the vector identities, and then directly substitute it in $$\nabla(\nabla\cdot \mathbf{A}) - \nabla\times \nabla \times \mathbf{A}$$, instead of substituting the metric elements in the equation above.


### Cartesian coordinates
Since $$h_1=h_2=h_3=1$$, all differentiations on these terms or the logarithm of these terms vanish. Therefore, the vector Laplacian is simply the component-wise scalar Laplacian

$$
(\nabla^2 \mathbf{A})_x = \nabla^2 A_x, \quad (\nabla^2 \mathbf{A})_y = \nabla^2 A_y, \quad (\nabla^2 \mathbf{A})_z = \nabla^2 A_z
$$

### Cylindrical coordinates
Substituting the metric elements with $$h_1=1$$, $$h_2=\rho$$ and $$h_3 = 1$$:

$$
\begin{aligned}
(\nabla^2 \mathbf{A})_\rho &= \nabla^2 A_\rho - \frac{1}{\rho^2}A_\rho - \frac{2}{\rho^2} \partial_\phi A_\phi \\
(\nabla^2 \mathbf{A})_\phi &= \nabla^2 A_\phi - \frac{1}{\rho^2} A_\phi + \frac{2}{\rho^2} \partial_\phi A_\rho\\
(\nabla^2 \mathbf{A})_z &= \nabla^2 A_z
\end{aligned}
$$

### Spherical coordinates
Substituting the metric elements with $$h_1=1$$, $$h_2=r$$ and $$h_3 = r\sin\theta$$:

$$
\begin{aligned}
(\nabla^2 \mathbf{A})_r &= \nabla^2 A_r - \frac{2}{r^2}A_r - \frac{2}{r^2\sin\theta}\partial_\theta(\sin\theta A_\theta) - \frac{2}{r^2\sin^2\theta}\partial_\phi A_\phi \\
(\nabla^2 \mathbf{A})_\theta &= \nabla^2 A_\theta - \frac{1}{r^2\sin\theta}A_\theta - \frac{2\cos\theta}{r^2\sin^2\theta}\partial_\phi A_\phi + \frac{2}{r^2}\partial_\theta A_r \\
(\nabla^2 \mathbf{A})_\phi &= \nabla^2 A_\phi - \frac{1}{r^2\sin^2\theta}A_\phi + \frac{2}{r^2\sin\theta}\partial_\phi A_r + \frac{2\cos\theta}{r^2\sin^2\theta}\partial_\phi A_\theta
\end{aligned}
$$

---
## Christoffel symbol

General vector gradient cannot be obtained from exterior differentiation alone. Therefore, the contraction between a vector gradient with another vector

$$
\mathbf{A} \cdot \nabla \mathbf{B}
$$

cannot be derived as above. This kind of term is commonly seen in e.g. Navier Stokes (the nonlinear term $$\mathbf{v}\cdot \nabla \mathbf{v}$$), induction equation in MHD, etc. Note the vector identity

$$
\mathbf{A}\cdot \nabla \mathbf{B} = \mathbf{A}(\nabla\cdot \mathbf{B}) - \nabla \times (\mathbf{A}_c\times \mathbf{B})
$$

where the subscript $$c$$ of $$\mathbf{A}$$ shows in this operation $$\mathbf{A}$$ is treated as a constant vector, although valid in Cartesian coordinates, no longer holds in general curvilinear coordinates. Most notably, a vector that is considered "constant" in the Cartesian frame (i.e. all derivatives vanish) is no longer constant in general curvilinear coordinates.

For the vector gradient, we need to introduce the Christoffel symbol, which is formalization of unit vector derivatives. Many of the derivations are from [Covariant derivative - Wikipedia](https://en.wikipedia.org/wiki/Covariant_derivative). To begin with, we see that any orthogonal curvilinear system we are considering is essentially a 3-D Riemannian manifold, embedded into Euclidean space via the position vector expressed as

$$
\Psi = \Psi(x^1, x^2, x^3)
$$

where $$x^i$$ are curvilinear coordinates. If $$\Psi$$ is explicitly written in Cartesian coordinates, then it would have the same form as in the beginning of [[#Metric]] section. Now we see the Jacobi matrix has another natural expression

$$\mathbf{J} = \frac{\partial \Psi}{\partial (x^1, x^2, x^3)}$$

and the metric tensor has elements given by

$$
g_{ij} = \left\langle \frac{\partial \Psi}{\partial x^i}, \frac{\partial \Psi}{\partial x^j}\right\rangle
$$

where the inner product can be interpreted as inner product in the Euclidean space. Assuming second-order continuous differentiability, the second-order derivative of $$\Psi$$ is related to its first order derivative via the Christoffel symbol

$$
\frac{\partial^2 \Psi}{\partial x^i \partial x^j} = \sum_k \Gamma_{ij}^k \frac{\partial \Psi}{\partial x^k}.
$$

Taking inner product with $$\partial \Psi/\partial x^l$$ on each side, it follows that the Christoffel symbol can be solved from the linear system

$$
\sum_k g_{kl} \Gamma_{ij}^{k} = \frac{1}{2}\left(\frac{\partial g_{il}}{\partial x^j} + \frac{\partial g_{jl}}{\partial x^i} - \frac{\partial g_{ij}}{\partial x^l}\right), \quad l,i,j \in \{1, 2, 3\}.
$$

For each $$(i,j)$$ pair, varying $$l$$ yields a linear system for $$\Gamma_{ij}^k$$. Denoting the inverse of the metric matrix as $$g^{km}g_{kl} = \delta_{ml}$$, we have

$$
\Gamma_{ij}^k = \frac{1}{2} \sum_l g^{kl} \left(\frac{\partial g_{il}}{\partial x^j} + \frac{\partial g_{jl}}{\partial x^i} - \frac{\partial g_{ij}}{\partial x^l}\right)
$$

From this alone we can conclude $$\Gamma_{ij}^k = \Gamma_{ji}^k$$, hence there are $$n^2(n+1)/2$$ independent components in $$n$$-dimensional space ($$18$$ in 3-D). For orthgonal curvilinear coordinates, the metric tensor is diagonal $$g_{ij} = g_{ii} \delta_{ij} = h_i^2 \delta_{ij}$$, and its inverse is simply taking the inverse of each diagonal element. Therefore we have the explicit form for Christoffel symbol in terms of $$h_i$$:

$$
\Gamma_{ij}^k = \frac{1}{h_k} \left(\frac{\partial h_k}{\partial x^j}\delta_{ik} + \frac{\partial h_k}{\partial x^i}\delta_{jk} - \frac{h_i}{h^k} \frac{\partial h_i}{\partial x^k}\delta_{ij}\right).
$$

With this we can proceed to derive the vector gradient. Firstly, note that $$\mathbf{e}_i = h_i^{-1} \partial \Psi/\partial x^i$$, an arbitrary vector can be written as

$$
\mathbf{A} = \sum_j A_j \mathbf{e}_j = \sum_j \frac{A_j}{h_j} \frac{\partial \Psi}{\partial x^j}.
$$

Its derivative w.r.t. $$x^i$$ is

$$
\begin{aligned}
\partial_i \mathbf{A} &= \sum_j \partial_i \left(\frac{A_j}{h_j}\right) \frac{\partial \Psi}{\partial x^j} + \sum_j \frac{A_j}{h_j} \frac{\partial^2 \Psi}{\partial x^i \partial x^j} \\ 
&= \sum_j \partial_i \left(\frac{A_j}{h_j}\right) \frac{\partial \Psi}{\partial x^j} + \sum_j \frac{A_j}{h_j} \sum_k \Gamma_{ij}^k \frac{\partial \Psi}{\partial x^k} \\ 
&= \sum_j \frac{\partial \Psi}{\partial x^j} \left[\partial_i \left(\frac{A_j}{h_j}\right) + \sum_k \Gamma_{ik}^j \frac{A_k}{h_k} \right]
\end{aligned}
$$

Assembling the derivatives, and writing the expression in a dyadic form

$$
\begin{aligned}
\nabla \mathbf{A} &= \sum_i \frac{\mathbf{e}_i}{h_i}\partial_i \mathbf{A} = \sum_i \frac{\mathbf{e}_i}{h_i} \sum_j \frac{\partial \Psi}{\partial x^j} \left[\partial_i \left(\frac{A_j}{h_j}\right) + \sum_k \Gamma_{ik}^j \frac{A_k}{h_k} \right] \\ 
&= \sum_{ij} \frac{h_j}{h_i} \left[\partial_i \left(\frac{A_j}{h_j}\right) + \sum_k \Gamma_{ik}^j \left(\frac{A_k}{h_k}\right) \right] \mathbf{e}_i\mathbf{e}_j.
\end{aligned}
$$

The contraction is hence a vector that can be easily expressed in terms of its components

$$
(\mathbf{A}\cdot \nabla \mathbf{B})_j = \sum_{i} A_i \frac{h_j}{h_i} \left[\partial_i \left(\frac{B_j}{h_j}\right) + \sum_k \Gamma_{ik}^j \left(\frac{B_k}{h_k}\right) \right].
$$

### Catersian coordinates
Because Cartesian coordinates define a flat space, not only $$h_1 = h_2 = h_3 = 1$$, but it follows that $$\Gamma_{ij}^k\equiv 0$$. Therefore the vector-gradient and its contraction

$$
\nabla \mathbf{A} = \sum_{ij}\partial_i A_j \mathbf{e}_i \mathbf{e}_j, \quad (\mathbf{A}\cdot \nabla \mathbf{B})_i = \sum_j A_i \partial_i B_j
$$

### Cylindrical coordinates
The Christoffel symbol for the cylindrical coordinates is given by

$$
\Gamma_{ij}^1 = \begin{bmatrix}
0 & 0 & 0 \\ 0 & -\rho & 0 \\ 0 & 0 & 0
\end{bmatrix},\quad 
\Gamma_{ij}^2 = \begin{bmatrix}
0 & \rho^{-1} & 0 \\ \rho^{-1} & 0 & 0 \\ 0 & 0 & 0
\end{bmatrix}, \quad 
\Gamma_{ij}^3 = \mathbf{0}
.
$$

Hence the vector gradient in its dyadic form

$$
\nabla \mathbf{A} = \begin{bmatrix} \mathbf{e}_\rho \\ \mathbf{e}_\phi \\ \mathbf{e}_z \end{bmatrix}^T
\begin{bmatrix} 
\partial_\rho A_\rho & \partial_\rho A_\phi & \partial_\rho A_z \\
\frac{1}{\rho}(\partial_\phi A_\rho - A_\phi) & \frac{1}{\rho}(\partial_\phi A_\phi + A_\rho) & \frac{1}{\rho} \partial_\phi A_z \\
\partial_z A_\rho & \partial_z A_\phi & \partial_z A_z
\end{bmatrix}
\begin{bmatrix} \mathbf{e}_\rho \\ \mathbf{e}_\phi \\ \mathbf{e}_z \end{bmatrix}
$$

### Spherical coordinates
The Christoffel symbol for the spherical coordinates is given by

$$
\Gamma_{ij}^1 = \begin{bmatrix}
0 & 0 & 0 \\ 0 & -r & 0 \\ 0 & 0 & -r\sin^2\theta
\end{bmatrix},\quad 
\Gamma_{ij}^2 = \begin{bmatrix}
0 & r^{-1} & 0 \\ r^{-1} & 0 & 0 \\ 0 & 0 & -\sin\theta\cos\theta
\end{bmatrix}, \quad 
\Gamma_{ij}^3 = \begin{bmatrix}
0 & 0 & r^{-1} \\ 0 & 0 & \frac{\cos\theta}{\sin\theta} \\ r^{-1} & \frac{\cos\theta}{\sin\theta} & 0
\end{bmatrix}.
$$

Hence the vector gradient in its dyadic form

$$
\nabla \mathbf{A} = \begin{bmatrix} \mathbf{e}_r \\ \mathbf{e}_\theta \\ \mathbf{e}_\phi \end{bmatrix}^T
\begin{bmatrix} 
\partial_r A_r & \partial_r A_\theta & \partial_r A_\phi \\
\frac{1}{r}(\partial_\theta A_r - A_\theta) & \frac{1}{r} (\partial_\theta A_\theta + A_r) & \frac{1}{r}\partial_\theta A_\phi \\
\frac{1}{r\sin\theta}\partial_\phi A_r - \frac{1}{r}A_\phi & \frac{1}{r\sin\theta}\partial_\phi A_\theta - \frac{\cos\theta}{r\sin\theta}A_\phi & \frac{1}{r\sin\theta} \partial_\phi A_\phi +\frac{1}{r}A_r + \frac{\cos\theta}{r\sin\theta} A_\theta
\end{bmatrix}
\begin{bmatrix} \mathbf{e}_r \\ \mathbf{e}_\theta \\ \mathbf{e}_\phi \end{bmatrix}
$$

---
## Derivative of unit vectors

Christoffel symbol is closely related to differentiation of unit vectors under curvilinear coordinates. Once again consider the relation $$\mathbf{e}_i = h_i^{-1} \partial \Psi/\partial x^i$$. The derivative of $$\mathbf{e}_i$$ concerns second order derivatives of $$\Psi$$, which is linked to the first order derivatives (as well as unit vectors) via Christoffel symbol:

$$
\begin{aligned}
\partial_j \mathbf{e}_i &= \partial_j \left(\frac{1}{h_i}\frac{\partial \Psi}{\partial x^i}\right) = \frac{1}{h_i}\frac{\partial^2 \Psi}{\partial x^i\partial x^j} - \frac{\partial_j h_i}{h_i^2}\frac{\partial \Psi}{\partial x^i} \\
&= \frac{1}{h_i} \sum_k \Gamma_{ij}^k \frac{\partial \Psi}{\partial x^k} - \frac{\partial_j h_i}{h_i^2}\frac{\partial \Psi}{\partial x^i} 
= \sum_k \frac{h_k}{h_i} \Gamma_{ij}^k \mathbf{e}_k - \frac{\partial_j h_i}{h_i} \mathbf{e}_i \\
&= \sum_k \frac{h_k}{h_i} \Gamma_{ij}^k \mathbf{e}_k - \Gamma_{ij}^i \mathbf{e}_i = \sum_k \left(\frac{h_k}{h_i} - \delta_{ik}\right) \Gamma_{ij}^k \mathbf{e}_k
\end{aligned}
$$

### Cartesian coordinates
In a flat space with zero Christoffel symbols, we have

$$
\partial_j \mathbf{e}_i \equiv \mathbf{0}.
$$

### Cylindrical coordinates

$$
\frac{\partial (\mathbf{e}_\rho, \mathbf{e}_\phi, \mathbf{e}_z)}{\partial (\rho, \phi,z)} = 
\begin{bmatrix}
\mathbf{0} & \mathbf{e}_\phi & \mathbf{0} \\
\mathbf{0} & - \mathbf{e}_\rho & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{0}
\end{bmatrix}
$$

### Spherical coordinates

$$
\frac{\partial (\mathbf{e}_r, \mathbf{e}_\theta, \mathbf{e}_\phi)}{\partial (r, \theta, \phi)} = 
\begin{bmatrix}
\mathbf{0} & \mathbf{e}_\theta & \sin\theta \, \mathbf{e}_\phi \\
\mathbf{0} & - \mathbf{e}_r & \cos\theta \, \mathbf{e}_\phi \\
\mathbf{0} & \mathbf{0} & - \sin\theta \, \mathbf{e}_r - \cos\theta \, \mathbf{e}_\theta
\end{bmatrix}.
$$


