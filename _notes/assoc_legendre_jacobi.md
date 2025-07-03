---
layout: page
title: Associated Legendre function to one-sided Jacobi polynomial
description: An interesting observation - associated Legendre functions are just one-sided Jacobi polynomials in disguise - with some prefactors
importance: 1
date: 2025-07-03 12:30:00-0400
category: Maths
---

# Background

For a field $$f$$ bounded within a sphere expanded in cylindrical coordinates, what would it look like on the surface, expanded in spherical harmonics? Conversely, for a field on the surface of the sphere, what is its projection onto the cylindrical basis? In other words, expanding $$f$$ as

$$f = \sum_{m,n} f_{mn}^s s^m P_n^{(\alpha^s, \beta^s)}(2s^2 - 1) + \sum_{m,n} f_{mn}^a z s^m P_n^{(\alpha^a, \beta^a)}(2s^2 - 1) = \sum_{\ell,m} q_{\ell m} P_\ell^m(z)$$

where $$s = \sqrt{1 - z^2}$$, we want to know the transformation that links $$(f_{nm}^s, f_{nm}^a)$$ to $$q_{\ell m}$$, and vice versa.
These are the question of interest and its answer will be a necessary step in implementing the magnetic boundary condition in the $$\Psi$$G model, and has been partially done in @holdenried-chernoff_surface_2020. In this process, I stumbled upon a strange identity, which links the associated Legendre function to certain one-sided Jacobi polynomials in a one-to-one way. This is described here.

# Associated Legendre function to one-sided Jacobi polynomial

**Proposition**
Let $$z \in [-1, 1]$$. The associated Legendre function $$P_\ell^m$$ is related to the one-sided Jacobi polynomial $$P_n^{(\alpha, \beta)}$$ via

$$P_\ell^m(z) = \left\{\begin{aligned}
            &C_{\ell m} s^m P_n^{(-\frac{1}{2}, m)}(2s^2 - 1),\quad  \ell-m=2n \\
            &C_{\ell m} z s^m P_n^{(\frac{1}{2}, m)}(2s^2 - 1),\quad \ell-m=2n+1
        \end{aligned}\right.$$

where $$s = \sqrt{1 - z^2} \in [0,1]$$, $$\ell,m,n \in \mathbb{Z}^*$$ with $$\ell \geq m$$, and $$C_{\ell m}$$ is a constant depending on $$\ell$$ and $$m$$. Alternatively, introducing $$\chi(l,m)$$ as an indicator function for $$l-m$$ being odd number, i.e. $$\chi = 1$$ when $$\ell - m$$ is odd and zero otherwise, we can write this uniformly as

$$P_\ell^m(z) = C_{\ell m} z^\chi s^m P_n^{(\chi -\frac{1}{2}, m)}(2s^2 - 1).$$

***Proof***: We use brute-force to expand the associated Legendre function $$P_\ell^m$$ in closed form, where the trailing polynomial in $$z$$ is expanded

$$\begin{aligned}
    P_\ell^m(z) &= \frac{(-1)^m}{2^\ell \ell!} \left(1 - z^2\right)^{\frac{m}{2}} \frac{d^{\ell + m}}{dz^{\ell + m}} (z^2 - 1)^\ell \\ 
    &= C_{\ell m} s^m \frac{d^{\ell + m}}{dz^{\ell + m}} \sum_{k=0}^\ell (-1)^{\ell - k} \begin{pmatrix} \ell \\ k \end{pmatrix} z^{2k} &\qquad C_{\ell m} &= \frac{(-1)^m}{2^\ell \ell!} \\ 
    &= C_{\ell m} s^m \sum_{k\geq \frac{l+m}{2}}^\ell (-1)^{\ell - k} \begin{pmatrix} \ell \\ k \end{pmatrix} \frac{(2k)!}{(2k - \ell -m)!} z^{2k - \ell - m} &\qquad C_{\ell m} &= \frac{(-1)^m}{2^\ell \ell!}
\end{aligned}$$

Now let us introduce $$n$$, as the half difference between $$\ell$$ and $$m$$, i.e. $$n = \lfloor (l-m)/2 \rfloor$$. The spherical harmonic degree $$\ell$$ can then be written as $$\ell = m + 2n + \chi$$. Then

$$\begin{aligned}
    P_\ell^m(z) &= C_{\ell m} s^m \sum_{k = m+n+\chi}^{m+2n+\chi} (-1)^{m + 2n + \chi - k} \begin{pmatrix} m + 2n + \chi \\ k \end{pmatrix} \frac{(2k)! \, z^{2k - 2m - 2n - \chi}}{(2k - 2m - 2n - \chi)!} 
\end{aligned}$$

Let us now devise a change of summation variable, $$k = m + n + \chi + k'$$. Under this transformation,

$$\begin{aligned}
    P_\ell^m(z) &= C_{\ell m} s^m \sum_{k' = 0}^{n} (-1)^{n - k'} \begin{pmatrix} m + 2n + \chi \\ m + n + k' + \chi \end{pmatrix} \frac{(2(m+n+k+\chi))!}{(2k' + \chi)!} z^{2k' + \chi} \\ 
    &= C_{\ell m} z^\chi s^m \sum_{k = 0}^{n} (-1)^{n - k} \frac{(m + 2n + \chi)!(2(m+n+k+\chi))!}{(m + n + k + \chi)!(n-k)!(2k + \chi)!} z^{2k} \\ 
    &= C_{\ell m} z^\chi s^m \sum_{k = 0}^{n} (-1)^{n - k} 2^{2(m+n)+\chi} \frac{(m + 2n + \chi)! \, \Gamma(m+n+k+\chi+\frac{1}{2})}{(n-k)! \, k! \, \Gamma(k + \chi + \frac{1}{2})} z^{2k}
\end{aligned}$$

where we used the property of the gamma function,

$$\frac{(2k)!}{k!} = 2^{2k} \frac{\Gamma(k+\frac{1}{2})}{\Gamma(\frac{1}{2})}, \qquad \forall k \in \mathbb{Z}_{\geq 0}.$$

We can just rearrange the terms, making some aesthetic simplification, and collect the constant prefactor, writing it as

$$\begin{aligned}
    P_\ell^m(z) &= A_{nm} z^\chi s^m \sum_{k = 0}^{n} \begin{pmatrix} n \\ k \end{pmatrix} \frac{\Gamma(m+n+k+\chi+\frac{1}{2})}{\Gamma(k + \chi + \frac{1}{2})} (-z^2)^{k}
\end{aligned}$$

where the constant prefactor is now given by

$$\begin{aligned}
    A_{n m} &= (-1)^{m+n} \frac{2^{2(m+n)+\chi}}{2^\ell \ell!} \frac{(m + 2n + \chi)!}{n!} = (-1)^{m+n} \frac{2^m}{n!} \\ 
\end{aligned}$$

The current form of the associated Legendre polynomial is close enough to the Jacobi polynomials, which have the following series expansion with argument $$2s^2 - 1 = 1 - 2z^2$$,

$$P_n^{(\chi - \frac{1}{2}, m)}(1 - 2z^2) = B_{nm} \sum_{k=0}^n \begin{pmatrix} n \\ k \end{pmatrix} \frac{\Gamma(m + n + k + \chi + \frac{1}{2})}{\Gamma(k + \chi + \frac{1}{2})} (-z^2)^k$$

where the constant prefactor is

$$B_{nm} = \frac{\Gamma(\chi + n + \frac{1}{2})}{n! \Gamma(\chi + m + n + \frac{1}{2})}$$

Assembling the factors $$z^\chi s^m$$, we retrieve the identity between associated Legendre function and the one-sided Jacobi polynomial

$$P_\ell^m(z) = C_{nm} z^\chi s^m P_n^{(\chi - \frac{1}{2}, m)}(2s^2 - 1)$$

with constant

$$C_{nm} = \frac{A_{nm}}{B_{nm}} = (-1)^{m+n} 2^{m} \frac{\Gamma(m + n + \chi + \frac{1}{2})}{\Gamma(n + \chi + \frac{1}{2})}.\qquad \text{Q.E.D.}$$

This relation has been validated by numerical calculations.

# Implications

This strange little identity associates $$P_\ell^m(z)$$ with exactly one $$z^\chi s^m P_n^{(\chi - \frac{1}{2}, m)}(2s^2 - 1)$$.
As indicated in the title, this relation is likely of little use elsewhere. In the cylindrical to spherical transforms that we need in $$\Psi$$G model and other QG models, both of these bases are natural basis functions in their respective coordinate systems. Outside of this domain, such transforms may be of little use. Therefore I have never seen such relation in any standard special function books or online resources.

The implication for our problem is that, if we consider the relation

$$f = \sum_{m,n} f_{mn}^s s^m P_n^{(-\frac{1}{2}, m)}(2s^2 - 1) + \sum_{m,n} f_{mn}^a z s^m P_n^{(\frac{1}{2}, m)}(2s^2 - 1) = \sum_{\ell,m} q_{\ell m} P_\ell^m(z)$$

the transform matrix $$\mathbf{M}_s^c$$ (meaning spherical to cylindrical), defined by

$$\mathbf{f} = \mathbf{M}_s^c \mathbf{q}$$

is particularly simple. In fact, if we arrange the coordinates accordingly such that they are grouped by their symmetry with respect to the equatorial plane, i.e.

$$\mathbf{f} = \begin{pmatrix} \mathbf{f}^s \\ \mathbf{f}^a \end{pmatrix}, \qquad 
    \mathbf{q} = \begin{pmatrix} \mathbf{q}_{\ell - m =2n} \\ \mathbf{q}_{\ell - m = 2n+1} \end{pmatrix}$$

then $$\mathbf{M}_s^c$$ is simply diagonal. As a result, its, the cylindrical to spherical tranform $$\mathbf{M}_c^s$$, is also diagonal.

For other choices of $$\alpha$$ and $$\beta$$, notice the identity concerning Jacobi polynomials

$$\begin{gathered}
    (2n + \alpha + \beta + 1) P_n^{(\alpha, \beta)} = (n + \alpha + \beta + 1) P_n^{(\alpha, \beta + 1)} + (n + \alpha) P_{n-1}^{(\alpha, \beta + 1)} \\ 
    (2n + \alpha + \beta + 1) P_n^{(\alpha, \beta)} = (n + \alpha + \beta + 1) P_n^{(\alpha + 1, \beta)} - (n + \beta) P_{n-1}^{(\alpha + 1, \beta)}
\end{gathered}$$

Hence if we choose in equation (1) $$\alpha^s + \frac{1}{2}, \alpha^a - \frac{1}{2}, \beta^s - m, \beta^a - m \in \mathbb{Z}_{\geq 0}$$, then the resulting transform matrix $$\mathbf{M}_s^c$$ will be banded, with upper triangular bands. The intuition is that now one associated Legendre polynomial is \"spread\" to $$P_n^{(\alpha, \beta)}$$ and several of its adjacent lower degrees ($$n$$), but not to all lower degree polynomials. The inverse $$\mathbf{M}_c^s$$ at this point is unfortunately already dense upper triangular; each one-sided Jacobi polynomial will have its signature in all associated Legendre polynomials up to a certain degree $$l$$, defined by $$l = m + 2n + \chi$$.

In the most general case, both $$\mathbf{M}_{c}^s$$ and $$\mathbf{M}_s^c$$ are dense upper triangular. Each $$P_\ell^m$$ will induce all one-sided Jacobi polynomials with $$n$$ up to the degree $$\lfloor (l-m)/2 \rfloor$$, and each one-sided Jacobi polynomial will induce all $$P_\ell^m$$ with $$\ell$$ up to the degree $$m + 2n + \chi$$. Note however that these are of course still band-limited, in the sense that the modes induced have a truncation degree in each direction ($$c\rightarrow s$$ and $$s\rightarrow c$$), hence the matrices are always upper triangular. This is of course expected because deep down (stripping off all the $$s$$ and $$z$$ prefactors in each basis), the transform is just between two set of polynomials with their respective orthogonality. Therefore any polynomial should be representable by another set of orthogonal polynomial up to a certain truncation level (i.e. the band width).


