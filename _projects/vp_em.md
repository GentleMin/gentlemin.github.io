---
layout: page
title: Simultaneous inversion of source and conductivity
description: Master thesis (2022)
img: assets/img/em/Model_recovery__Q-VP.png
importance: 8
attachment: em_vp.pdf
category: Geomagnetism
---

Time-varying electromagnetic field observed on the ground or at a spacecraft consists of contributions from inducing electric currents, as well as induced currents in the conductive Earth’s interior by virtue of electromagnetic induction. Knowledge about the spatio-temporal structure of inducing currents is a key component in ionospheric and magnetospheric studies and is also needed in space weather hazard evaluation, whereas the induced currents are sensitive to the Earth’s subsurface electrical conductivity distribution and allow us to probe this physical property. This thesis presents an approach that reconstruct the inducing source and subsurface conductivity structures simultaneously, preserving the consistency between the inducing and induced currents by exploiting the physical link between them. To achieve this, the underlying inverse problem is formulated as a separable nonlinear least squares (SNLS) problem, where the inducing current and the subsurface conductivity enter as linear and non-linear model unknowns, respectively. The SNLS problem is solved with the variable projection method and compared with other conventional approaches. The feasibility of this approach is demonstrated via experiments where the ionospheric and magnetospheric currents along with a 1-D average mantle conductivity distribution are simultaneously reconstructed from the ground magnetic observatory data.

This project was finished in 2022 as Master thesis under the supervision of Dr. Alexander Grayver.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/em/vp_abstract.png" title="graphic abstract" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Schematic plot of how the inducing source and the subsurface conductivity are simultaneously inverted.
</div>

### Resources and downloads
- [Repo] For the code please contact the authors. The repo is located in Alexander's private GitHub project, and cannot be easily made public.
- [PDF] <a href="{{ 'assets/pdf/em_vp.pdf' | relative_url }}">Original master thesis</a>. It is recommended to view the publication (see below) on *Earth Planets and Space* since there are quite some updated contents after the thesis.
- [PDF] <a href="https://doi.org/10.1186/s40623-023-01816-5">Published work</a> on *Earth Planets and Space*. PDF version <a href="{{ 'assets/pdf/Min_Grayver__2023.pdf' | relative_url }}">download</a>.
- [PDF] <a href="{{ 'assets/pdf/EM_inversion_with_VP__IUGG__MinJingtao.pdf' | relative_url }}">Presentation slides for this work at IUGG 2023</a>. Adobe acrobat recommended as the presentation contains a video snippet.
<br />


