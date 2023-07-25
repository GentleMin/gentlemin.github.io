---
layout: page
title: Alfvén waves
description: Alfvén waves, dispersion relations in ideal and diffusive medium; Hartmann boundary layer.
importance: 1
date: 2023-07-24 12:00:00-0400
category: Physics
---

Alfvén waves are magnetohydrodynamic (MHD) waves with Lorentz force (or
the magnetic tension) as restoring force. In this section I review some
of the key aspects of this type of ways, including the equations,
dispersion relations, phase and group velocities, etc.

## Governing equations

I start by stating the governing equations of the system. Here it is
already assumed that the medium is both homogeneous and incompressible,
so that 

$$\nabla\cdot \mathbf{u} = 0,\quad \rho \equiv Cst.$$

which
already filters out all acoustic waves and stratification / arbitrary
heterogeneity of the setup. @ferraro_reflection_1954 has a short section
on Alfvén waves in stratified atmosphere, where the wave solution takes
the form of Bessel functions, and is shown to be damped as it enters
stratification region. This might be important in stars, planetary
atmosphere, and might also become important if similar stratification
occurs in Earth's core. When the incompressibility assumption is
dropped, one obtains *magneto-acoustic* (*magnetosonic*) waves, which
are hybrid between MHD waves and acoustic waves, with wave velocities in
between Alfvén waves and acoustic waves. When both the fluctuation in
density and the volumetric strain rate are comparatively negligible (),
the assumptions should still work, and it should suffice in studying the
reflection and transmission near the boundary.

I start from Navier-Stokes equation and induction equation in a
homogeneous medium,

$$\frac{\partial \mathbf{u}}{\partial t} + \mathbf{u}\cdot \nabla \mathbf{u} = - \nabla \frac{P}{\rho} + \frac{1}{\rho \mu_0} (\nabla\times \mathbf{B})\times \mathbf{B} + \nu \nabla^2 \mathbf{u},$$

$$\frac{\partial \mathbf{B}}{\partial t} = \nabla\times (\mathbf{u}\times \mathbf{B}) + \eta \nabla^2 \mathbf{B}.$$
The total fields ($$\mathbf{u}$$, $$\mathbf{B}$$) are decomposed into
background fields ($$\mathbf{U}_0$$, $$\mathbf{B}_0$$) and perturbation
fields ($$\mathbf{u}$$, $$\mathbf{b}$$). We take the background velocity
field to be zero ($$\mathbf{U}_0 = \mathbf{0}$$), so that no advection
occurs. The magnetic background field $$\mathbf{B}_0$$ is a constant in
both space and time, representing a time-invariant uniform field. This
approximation should hold as long as both the characteristic time scale
and the length scale of $$\mathbf{B}_0$$ are much larger than those of the
perturbed fields (in fact, the ratio should be greater than
$$|\mathbf{B}_0|/|\mathbf{b}|$$).

To linearize the set of equations, the perturbation magnetic field is
considered much smaller than the background field
($$|\mathbf{b}|\ll |\mathbf{B}_0|$$), and the perturbation velocity field
is at the same order of magnitude as magnetic field, in the sense that
$$|\mathbf{u}|\sim |\mathbf{b}|/\sqrt{\rho \mu_0}$$. Collecting only the
first order terms, we obtain the linearized system 

$$\begin{aligned}
    \frac{\partial \mathbf{u}}{\partial t} &= - \nabla \frac{P}{\rho} + \frac{1}{\rho \mu_0} (\nabla\times \mathbf{b})\times \mathbf{B}_0 + \nu \nabla^2 \mathbf{u}, \\
    \frac{\partial \mathbf{b}}{\partial t} &= \nabla\times (\mathbf{u}\times \mathbf{B}_0) + \eta \nabla^2 \mathbf{b}.
\end{aligned}$$

which can be further rearranged into a more symmetric
form using vector identities

$$\frac{\partial \mathbf{u}}{\partial t} = \frac{1}{\rho \mu_0} \mathbf{B}_0 \cdot \nabla \mathbf{b} + \nu \nabla^2 \mathbf{u} - \nabla P_\mathrm{eff}',$$

$$\frac{\partial \mathbf{b}}{\partial t} = \mathbf{B}_0 \cdot \nabla \mathbf{u} + \eta \nabla^2 \mathbf{b}.$$
where the effective pressure is a sum of mechanical pressure and the
magnetic pressure, divided by the density of the medium

$$P'_\mathrm{eff} = \frac{P}{\rho} + \frac{\mathbf{B}_0\cdot \mathbf{b}}{\rho \mu_0}.$$

The total magnetic pressure is of course
$$(\mathbf{B_0} + \mathbf{b})^2/2\rho \mu_0$$, but given the previous
assumption that $$\mathbf{B}_0$$ is constant vector, and only the
first-order terms are retained, using $$(\mathbf{B}_0 + \mathbf{b})^2$$ in
the numerator would be equivalent to stating
$$2\mathbf{B}_0\cdot \mathbf{b}$$, which is what has been obtained
directly from $$(\nabla\times \mathbf{b})\times \mathbf{B}_0$$.

## Dispersion relation of the ideal system

Neglecting the pressure gradient, and neglecting the viscous as well as
magnetic diffusion, the equations can be combined into a second-order
wave equation, in the form

$$\frac{\partial^2 \mathbf{u}}{\partial t^2} = \frac{(\mathbf{B}_0\cdot \nabla)^2}{\rho \mu_0} \mathbf{u},\qquad \frac{\partial^2 \mathbf{b}}{\partial t^2} = \frac{(\mathbf{B}_0\cdot \nabla)^2}{\rho \mu_0} \mathbf{b},$$

which, with a plane wave ansatz of any sort (equivalently converting the
equation into frequency-wavenumber domain), immediately yields the
dispersion relation for Alfvén waves in diffusionless medium

$$\omega^2 = \frac{1}{\rho \mu_0} \left(\mathbf{k}\cdot \mathbf{B}_0\right)^2 = \frac{B_0^2}{\rho \mu_0} \left(\mathbf{k}\cdot \widehat{\mathbf{B}}_0\right)^2 = V_A^2 \left(\mathbf{k}\cdot \widehat{\mathbf{B}}_0\right)^2.$$

where $$\widehat{\mathbf{B}}_0$$ is the unit vector in the direction of
$$\mathbf{B}_0$$, and $$V_A = B_0/\sqrt{\rho \mu_0}$$ is the Alfvén wave
velocity, as will become clearer in the next section. For the plane wave
ansatz used in this article, please refer to
eq.([\[eqn:wave-ansatz\]](#eqn:wave-ansatz){reference-type="ref"
reference="eqn:wave-ansatz"}) and the related texts in the remark box.
Since reversing the sign on $$\omega$$ and $$\mathbf{k}$$ simultaneously
would yield the same physical solution (taking the real part of the
complex wave yields the exact same expression, see remark box that
follows), when describing the plane waves I shall take the convention
that $$\omega > 0$$. Under this convention the dispersion relation can be
further written as 

$$
    \omega = \pm V_A \left(\mathbf{k}\cdot \widehat{\mathbf{B}}_0\right) = 
    \left\{\begin{aligned}
        V_A \left(\mathbf{k}\cdot \widehat{\mathbf{B}}_0\right),\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 > 0 \\ 
        - V_A \left(\mathbf{k}\cdot \widehat{\mathbf{B}}_0\right),\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 < 0
    \end{aligned}\right.
$$

The two solutions for $$\omega$$ correspond to
two propagation directions of the Alfvén wave. As will also become clear
later, Alfvén waves can either propagate in or opposite the direction of
the background magnetic field, which corresponds to the obtained two
solutions.

It is already readily seen that Alfvén wave is an anisotropic wave. The
isotropy is broken due to the fact that background magnetic field is the
essential cornerstone for providing the magnetic tension, and the
orientation of the magnetic field has a special status. It will also be
seen that the orientation of the background magnetic field greatly
complicates the reflection-refraction problem, compared to the isotropic
waves, such as elastic waves, acoustic waves (seismic waves) and light
waves in isotropic medium. The anisotropy dictates that, for a given
temporal frequency $$\omega$$,

$$\Big|\mathbf{k}\cdot \widehat{\mathbf{B}}_0\Big| = \frac{\omega}{V_A}$$

meaning the wave vector has a fixed projection length on the background
field.

::: mdframed
In this article I shall use the following convention for plane wave

$$
    \mathbf{A}(\mathbf{r}, t) = \mathbf{A}_0 \exp\left\{i\left(\omega t - \mathbf{k}\cdot \mathbf{r}\right)\right\},$$

and the conventions for respective Fourier transforms follow. Some
intermediate steps and results in this article will be different by a
sign compared to the alternative ansatz
$$\exp\{i(\omega t + \mathbf{k}\cdot \mathbf{r})\}$$, for instance the
dispersion relation as shown in
eq.([\[eqn:dispersion-ideal\]](#eqn:dispersion-ideal){reference-type="ref"
reference="eqn:dispersion-ideal"}). In the other convention,
$$\mathbf{k}$$ is opposite the direction in which the phase propagates,
and $$\omega = V_A (\mathbf{k}\cdot \widehat{\mathbf{B}}_0)$$ would
represent a wave travelling in the opposite direction of $$\mathbf{B}_0$$.

In the ideal case without diffusion, it can be easily shown that the
perturbation velocity field $$\mathbf{u}$$ and the magnetic field
$$\mathbf{b}$$ are proportional to one another. To this end, we can
construct a plane wave solution for the perturbed fields

$$\mathbf{b} = \mathbf{b}_0 \exp\{i(\omega t - \mathbf{k}\cdot \mathbf{r})\}, \quad \mathbf{u} = \mathbf{u}_0 \exp\{i(\omega t - \mathbf{k}\cdot \mathbf{r})\}.$$

The two waves share the same phase argument since their phases need to
match in the coupled system of equations. Substituting the expression
into the first-order ideal equation yields

$$\frac{\partial \mathbf{u}}{\partial t} = \frac{\mathbf{B}_0\cdot \nabla}{\rho \mu_0} \mathbf{b},\quad \Longrightarrow\quad i\omega \mathbf{u}_0 = - i \frac{\mathbf{B}_0\cdot \mathbf{k}}{\rho \mu_0} \mathbf{b}_0\quad \Longrightarrow\quad \mathbf{u}_0 = -\frac{V_A (\mathbf{k}\cdot \widehat{\mathbf{B}}_0)}{\omega\sqrt{\rho \mu_0}} \mathbf{b}_0.$$

Taking into account the dispersion relation, we have

$$\mathbf{u}_0 = \left\{\begin{aligned}
        - \frac{\mathbf{b}_0}{\sqrt{\rho \mu_0}},\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 > 0,\\
        \frac{\mathbf{b}_0}{\sqrt{\rho \mu_0}},\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 < 0.
\end{aligned}\right.$$

Therefore, the perturbed magnetic field and
the velocity field are opposite one another (or have a $$\pi$$ phase
shift) when the wave is propagating in the same direction of the
background magnetic field, and the perturbed fields are completely
in-phase when the wave is propagating in the opposite direction of
$$\mathbf{B}_0$$. Either way, the magnetic field and the velocity field in
Alfvén waves share the same polarization.
:::

## Dispersion relation of the diffusive system

With viscous and magnetic diffusion, the system of equations cannot be
easily combined into one wave equation. Instead, the system of equations
can be converted directly into frequency-wavenumber domain

$$\begin{aligned}
    i\omega \mathbf{u} &= -i\frac{\mathbf{B}_0\cdot \mathbf{k}}{\rho \mu_0} \mathbf{b} - \nu k^2 \mathbf{u}, \\ 
    i\omega \mathbf{b} &= -i(\mathbf{B}_0\cdot \mathbf{k}) \mathbf{u} - \eta k^2 \mathbf{b},
\end{aligned}$$

which can be rearranged into the linear system

$$\begin{aligned}
    (i\omega + \nu k^2) \mathbf{u} + i\frac{\mathbf{B}_0\cdot \mathbf{k}}{\rho \mu_0} \mathbf{b} = \mathbf{0}, \\ 
     i(\mathbf{B}_0\cdot \mathbf{k}) \mathbf{u} + (i\omega + \eta k^2) \mathbf{b} = \mathbf{0}.
\end{aligned}$$

Naturally, for the system to have nontrivial solutions,
the necessary condition is 

$$\det \begin{pmatrix}
        i\omega + \nu k^2 & i \frac{\mathbf{B}_0 \cdot \mathbf{k}}{\rho \mu_0} \\ 
        i (\mathbf{B}_0 \cdot \mathbf{k}) & i\omega + \eta k^2
    \end{pmatrix} = - \omega^2 + i(\nu + \eta) k^2 \omega + \frac{(\mathbf{B}_0\cdot \mathbf{k})^2}{\rho \mu_0} + \nu \eta k^4 0$$

which is the dispersion relation for the diffusive system. The relation
can be rearranged as a biquadratic polynomial equation of $$k$$,

$$
    \nu \eta k^4 + \left(V_A^2 \cos^2\gamma + i\omega(\nu + \eta)\right) k^2 - \omega^2 = 0
$$

where I have used $$\gamma = \langle \mathbf{B}_0, \mathbf{k} \rangle$$,
and the defined Alfvén wave velocity $$V_A = B_0 / \sqrt{\rho \mu_0}$$.
The roots of this equation give the spatial branch of the dispersion
relations

$$k^2 = -\frac{V_A^2 \cos^2\gamma}{2\nu\eta} \left(1 + i\frac{\omega(\nu + \eta)}{V_A^2\cos^2\gamma}\right) \left[1 \pm \sqrt{1 + \frac{4\omega^2 \nu \eta}{V_A^4 \cos^4\gamma \left(1 + \frac{i\omega(\nu + \eta)}{V_A^2 \cos^2\gamma}\right)^2}}\right].$$

The repetitive terms can be greatly simplified by introducing the
notation 

$$\mathrm{S}_\omega = \frac{2V_A^2}{\omega (\nu + \eta)}$$

and
the spatial branch of the dispersion relation can be rewritten as

$$
    k^2 = - \frac{V_A^2}{2\nu \eta} \left(\cos^2\gamma + i2\mathrm{S}_\omega^{-1}\right) \left[1 \pm \sqrt{1 + \frac{4\omega^2 \nu \eta}{V_A^4 \left(\cos^2\gamma + i2\mathrm{S}_\omega^{-1}\right)^2}}\right]
$$

The notation $$\mathrm{S}_\omega$$ defined as such represents the ratio
between the diffusion time scale and the Alfvén wave time scale, and is
called the *Lundquist number*. In its general form, without specifying
the length scale of interest, the Lundquist number is written as

$$\mathrm{S} = \frac{\tau_\alpha}{\tau_A} = \frac{L^2/\alpha}{L/V_A} = \frac{V_A L}{\alpha}.$$

Choosing specific diffusion mechanism (specifying $$\alpha$$) and specific
time scale (specifying $$L$$) yields a variety of variants of Lundquist
number. In this case, we see that the diffusion mechanism of interest is
the combined effect of viscous diffusion and magnetic diffusion; the
length scale of interest is determined by the Alfvén wavelength at
specified frequency, i.e.

$$\alpha \sim \frac{\nu + \eta}{2},\quad L \sim \frac{V_A}{\omega}\quad \Longrightarrow\quad \mathrm{S}_\omega = \frac{V_A^2/\omega}{(\nu + \eta)/2} = \frac{2V_A^2}{\omega(\nu + \eta)}.$$

When Lundquist number $$\mathrm{S}\gg 1$$, Alfvén wave time scale is much
smaller than that of diffusion time scale; this means the damping of
Alfvén waves at the specific length scale is small, and the propagation
of Alfvén waves is allowed in the system. When $$\mathrm{S} \ll 1$$,
diffusion time scale is much smaller, and diffusion process dominates
the system at given length scale, prohibiting the effective propagation
of Alfvén waves. This can be readily seen from the dispersion relation,
as follows.

At $$\mathrm{S}_\omega \ll 1$$, the term $$\mathrm{S}_\omega^{-1}$$ always
dominates over other terms, reducing
eq.([\[eqn:dispersion-spatial\]](#eqn:dispersion-spatial){reference-type="ref"
reference="eqn:dispersion-spatial"}) into the form

$$k^2 \approx - i \frac{V_A^2}{2\nu\eta} 2\mathrm{S}_\omega^{-1} \left(1 \pm \sqrt{1 - \frac{\omega^2 \nu \eta}{V_A^4}\mathrm{S}_\omega^2}\right) = -i \frac{\omega}{2\nu \eta} \left(\nu + \eta \pm |\nu - \eta|\right)$$

which gives the ultimate solutions

$$k_1^2 \approx -i \frac{\omega}{\min(\nu, \eta)},\quad k_1 = \pm \frac{1 - i}{\sqrt{2}}\sqrt{\frac{\omega}{\min(\nu,\eta)}},$$

$$k_2^2 \approx -i \frac{\omega}{\max(\nu, \eta)},\quad k_2 = \pm \frac{1 - i}{\sqrt{2}}\sqrt{\frac{\omega}{\max(\nu,\eta)}}.$$
These solutions correspond to damped oscillations, which decays in the
propagating direction. The characteristic decaying length is given by
$$\bar{\lambda}_1 = \sqrt{2\min(\nu,\eta)/\omega}$$ and
$$\bar{\lambda}_2 = \sqrt{2\max(\nu,\eta)/\omega}$$, respectively. The
$$\sqrt{\omega/\alpha}$$ scaling for $$k$$, the characteristic wavelength
scaling with $$\sqrt{\alpha/\omega}$$ and the feature of damped
oscillation reveal that these solutions correspond to *Stokes*-type
boundary layers. The oscillation and damping is simply governed by the
diffusion process, but not the magnetic tension.

At $$\mathrm{S}_\omega \gg 1$$, or
$$V_A^2 \gg \omega (\nu + \eta) \geq 2\omega \sqrt{\nu\eta}$$, we expect
to recover the regime where magnetic tension is important in the system,
producing the propagation of Alfvén waves. Given some value of $$\gamma$$
so that $$\cos\gamma \sim 1$$ is at some finite magnitude, the inverse
Lundquist number $$\mathrm{S}_\omega^{-1}$$ will always be small compared
to $$\cos^2\gamma$$. To see the effect of diffusion in the system we can
keep $$\mathrm{S}_\omega^{-1}$$ in
eq.([\[eqn:dispersion-spatial\]](#eqn:dispersion-spatial){reference-type="ref"
reference="eqn:dispersion-spatial"}) to its leading order,

$$\begin{aligned}
k^2 &= - \frac{V_A^2\cos^2\gamma}{2\nu\eta} \left(1 + i\frac{2}{\mathrm{S}_\omega\cos^2\gamma}\right) \left[1 \pm \sqrt{1 + \frac{4\omega^2 \nu\eta}{V_A^4 \cos^4\gamma}\left(1 + i\frac{2}{\mathrm{S}_\omega \cos^2\gamma}\right)^{-2}}\right] \\ 
&\approx - \frac{V_A^2\cos^2\gamma}{2\nu\eta} \left(1 + i\frac{2}{\mathrm{S}_\omega\cos^2\gamma}\right) \left[1 \pm \left(1 + \frac{2\omega^2 \nu\eta}{V_A^4 \cos^4\gamma}\left(1 - i\frac{4}{\mathrm{S}_\omega \cos^2\gamma}\right)\right)\right]
\end{aligned}$$

which gives two ultimate solutions

$$k_1^2 \approx - \frac{V_A^2}{\nu\eta} \left(\cos^2\gamma + i 2 \mathrm{S}_\omega^{-1}\right),\quad 
    k_1 \approx \pm \frac{V_A \cos\gamma}{\sqrt{\nu\eta}} \left(-\frac{1}{\mathrm{S}_\omega \cos^2\gamma} + i\right),$$

$$k_2^2 \approx \frac{\omega^2}{V_A^2\cos^2\gamma} \left(1 - i \frac{2}{\mathrm{S}_\omega \cos^2\gamma}\right),\quad k_2 \approx \pm \frac{\omega}{V_A \cos\gamma} \left(1 - i \frac{1}{\mathrm{S}_\omega \cos^2\gamma}\right).$$
The first solution $$k_1$$ has a dominant imaginary part. In the case
where $$\mathrm{S}_\omega^{-1} \ll 1$$ is negligible this can be simply
written as
$$k_1\approx \pm i V_A \cos\gamma/\sqrt{\nu\eta} = \pm i/\delta$$. This
correspond to a *Hartmann boundary layer*. Properties of this layer is
listed below.

::: mdframed
The thickness, or the characteristic length scale over which the wave
decays in a Hartmann layer, is given by

$$\delta_\mathrm{BL} = \frac{\sqrt{\nu\eta}}{V_A|\cos\gamma|} = \frac{\sqrt{\rho \mu_0 \nu \eta}}{B_0 |\cos\gamma|} = \frac{1}{B_\parallel}\sqrt{\frac{\rho \nu}{\sigma}}.$$

Here $$B_\parallel = |{B}_0\cdot \hat{\mathbf{k}}|$$ is the magnetic field
strength in line with the wave vector. The boundary layer thickness
scales with $$\sqrt{\nu\eta}/V_A$$, and hence goes to zero when
$$\nu,\eta \rightarrow 0$$. Nevertheless, an infinitely small Hartmann
layer might be able to accommodate finite velocity and magnetic field
discontinuity at the boundary (), just like the free-slip boundary
condition for inviscid fluid. The reason for that is the infinite
conductivity assumption, which allows infinitely large current in the
system, giving rise to magnetic field discontinuity. This boundary layer
seems to play an important role in constructing solutions that satisfy
continuity boundary conditions across the interface
[@schaeffer_reflection_2012], even at high Lundquist numbers.

The thickness of the Hartmann boundary layer is another important length
scale of the system. When variation occurs on a length scale comparable
to or smaller than $$\delta_\mathrm{BL}$$, the viscous and magnetic
diffusion wins over, and promotes boundary layer behaviour; when the
length scale of variation is much larger than $$\delta_\mathrm{BL}$$, the
magnetic tension is much more effective. This motivates the introduction
of a dimensionless number, *Hartmann number*, which, supposedly, is the
ratio of Lorentz force to viscous force. It can also be interpreted as
the ratio of some characteristic length scale to the Hartmann layer
thickness

$$
\mathrm{Ha} = B L \sqrt{\frac{\sigma}{\rho\nu}} = \frac{L}{\delta_\mathrm{BL}}.
$$

For Hartmann layer, the amplitudes of $$\mathbf{u}$$ and $$\mathbf{b}$$
follow a relation different from the travelling wave solution. Recall at
high Lundquist number, $$V_A^2 \gg \omega \eta$$, the first-order equation
gives

$$
\mathbf{u} = \frac{i \mathbf{B}_0\cdot \mathbf{k}}{\rho \mu_0 (i\omega + \nu k^2)} \mathbf{b} \approx \frac{\mp B_0 \frac{V_A \cos^2\gamma}{\sqrt{\nu\eta}}}{\rho \mu_0 \frac{V_A^2}{\eta}\cos^2\gamma} \mathbf{b} = \mp \sqrt{\frac{\eta}{\nu}}\frac{\mathbf{b}}{\sqrt{\rho \mu_0}}  = \mp \mathrm{Pm}^{-1/2} \frac{\mathbf{b}}{\sqrt{\rho\mu_0}}
$$

where $$\mathrm{Pm} = \frac{\nu}{\eta}$$ is the magnetic Prandtl number.
Not surprisingly, the amplitude in such boundary layer is skewed towards
the field with smaller diffusion.
:::

The second solution $$k_2$$ reduces to the dispersion relation of Alfvén
waves in diffusionless medium, i.e. $$k_2 = \pm \omega/V_A \cos\gamma$$,
when $$\mathrm{S}_\omega^{-1}$$ is dropped from the multiplier
(eq.[\[eqn:dispersion-ideal\]](#eqn:dispersion-ideal){reference-type="ref"
reference="eqn:dispersion-ideal"}). To first order, the role of
non-negligible diffusion is to introduce damping with the coefficient
$$1/\mathrm{S}_\omega \cos^2\gamma = \omega(\nu+\eta)/2V_A^2\cos^2\gamma$$,
which mildly damps the Alfvén wave as it propagates.

At the mildly diffusive limit $$\mathrm{S}_\omega \gg 1$$, both solutions
are anisotropic. For the Hartmann boundary layer solution, the thickness
or spatial decay rate is constrained by the projection of magnetic field
on the wave vector. For the travelling Alfvén wave solution, the
wavenumber is also determined by the projection of the magnetic field on
the wave vector. Conversely, it means the wave vectors in both solutions
are only controlled in the direction of the background field.

## Phase and group velocities

Phase velocity is the velocity at which the phase of a monochromatic
wave travels. Given that a plane wave takes the form
$$\exp(i(\omega t - \mathbf{k}\cdot \mathbf{r})) = \exp(i\mathbf{k}\cdot (\omega t \hat{\mathbf{k}} / k - \mathbf{r}))$$,
the phase velocity is given by

$$\mathbf{c}_p = \frac{\omega}{k}\hat{\mathbf{k}}.$$

Apparently, the
phase velocity always has the same direction as the wave vector. The
wave vector for plane wave is exactly the indicator of phase
propagation. When a collection of waves is present (in reality there is
almost never standalone monochromatic plane wave, since that implies
infinite energy), the velocity at which the wave packet near a frequency
travels is different from the phase velocity. This is called the group
velocity, and is given by 

$$\mathbf{c}_g = \nabla_k \omega.$$

Since wave
packets and wave groups are the carrier of information and energy, group
velocity is considered to be the velocity at which information and
energy propagates. Although this seems to be true in many cases, I argue
that this cannot replace the energy argument. Group velocity is a
mathematical property, a property that arises due to the mathematical
form of wave ansätze; energy flux is a physical property, which does not
seem to be strictly linked to the wave ansatz *a priori*.

Both phase velocity and the group velocity can be derived from the
dispersion relations. The dispersion relation with finite
$$\mathrm{S}_\omega$$ is complicated, and would give rise to dispersive
waves. The Alfvén wave in ideal, diffusionless medium, however, is
simple. The phase velocity is given by 

$$
    \mathbf{c}_p = \frac{\omega}{k} \hat{\mathbf{k}} = 
    \left\{\begin{aligned}
        V_A (\hat{\mathbf{k}}\cdot \widehat{\mathbf{B}}_0) \hat{\mathbf{k}} = V_A \cos\gamma \, \hat{\mathbf{k}} = \frac{\mathbf{B}_0\cdot \hat{\mathbf{k}}}{\sqrt{\rho \mu_0}} \hat{\mathbf{k}},\quad \mathbf{k} \cdot \widehat{\mathbf{B}}_0 > 0 \\
        - V_A (\hat{\mathbf{k}}\cdot \widehat{\mathbf{B}}_0) \hat{\mathbf{k}} = -V_A \cos\gamma \, \hat{\mathbf{k}} = - 
        \frac{\mathbf{B}_0\cdot \hat{\mathbf{k}}}{\sqrt{\rho \mu_0}} \hat{\mathbf{k}},\quad \mathbf{k} \cdot \widehat{\mathbf{B}}_0 < 0 
    \end{aligned}\right.
$$

which can be uniformly written as

$$\mathbf{c}_p = V_A |\cos\gamma| \, \hat{\mathbf{k}}.$$

The magnitude
of the phase velocity of Alfvén wave is fixed, as long as the
orientation of the wave propagation is fixed. In this sense, Alfvén wave
is diffusionless. Among all the direction of waves, the wave that
propagates along the background field propagates the fastest.

For isotropic waves such as seismic waves and light waves in isotropic
medium, not only are the waves dispresionless, but
$$\mathbf{c}_p \parallel \mathbf{c}_g$$. This is not the case for
anisotropic waves as Alfvén wave. While the phase can travel in any
direction except normal to the background field, the group velocity is
always aligned with the background field 

$$
    \mathbf{c}_g = \nabla_k \omega = 
    \left\{\begin{aligned}
        V_A \widehat{\mathbf{B}}_0 = \frac{\mathbf{B}_0}{\sqrt{\rho \mu_0}},\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 > 0, \\ 
        - V_A \widehat{\mathbf{B}}_0 = - \frac{\mathbf{B}_0}{\sqrt{\rho \mu_0}},\quad \mathbf{k}\cdot \widehat{\mathbf{B}}_0 < 0.
    \end{aligned}\right.
$$

For an Alfvén wave propagating (in the sense
of $$\mathbf{c}_p$$ or $$\mathbf{k}$$) in the direction that forms an angle
$$\gamma < \pi/2$$ with the magnetic field $$\mathbf{B}_0$$, i.e. downwind,
the group velocity is *in* the direction of $$\mathbf{B}_0$$. For an
Alfvén wave propagating upwind, the group velocity is *opposite* the
direction of $$\mathbf{B}_0$$. Either way, the magnitude of group velocity
is always given by the Alfvén wave velocity $$V_A$$.

## Energy and energy flux


