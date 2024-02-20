---
layout: page
title: Geomagnetic data assimilation under Plesio-Geostrophy
description: Ongoing project (2023-)
img: assets/img/em/malkus_eigenmode.png
importance: 5
category: Geomagnetism
---

Plesio-Geostrophy Model, or PG, is a reduced-dimensional model for 3-D magnetohydrodynamics (MHD) in rapidly rotating sphere.
This is proposed by [Jackson and Maffei (2020)](https://royalsocietypublishing.org/doi/10.1098/rspa.2020.0513), and also contituted part of the doctoral work of [Holdenried-Chernoff (2021)](https://www.research-collection.ethz.ch/handle/20.500.11850/509840).

The current ongoing implementation of PG model is the Python package [PlesioGeostroPy](https://github.com/GentleMin/PlesioGeostroPy).
Figure below visualizes an eigenmode solved using this code.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/em/malkus_eigenmode.png" title="malkus eigenmode" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<br />

---

### Theory paper and reference material
- Theory and concept paper, [Jackson and Maffei (2020)](https://royalsocietypublishing.org/doi/10.1098/rspa.2020.0513).
- Daria Holdenried-Chernoff's [doctoral thesis (2021)](https://www.research-collection.ethz.ch/handle/20.500.11850/509840).
<br />

---

### Formulation, documentation and results
- [PDF] <a href="{{ 'assets/pdf/PG_Ingredients.pdf' | relative_url }}">Formulations for PG model: missing ingredients and new recipes</a>. Recent updates:
  - Energy calculation: in progress
  - Multi-precision calculation: in progress
- [PDF] <a href="{{ 'assets/pdf/PG_Results.pdf' | relative_url }}">Results of the PG model.</a>. Recent updates:
  - Hydrodynamic results added, equations and numerical analysis complete.
  - Malkus field results added, equations complete.
  - Poloidal dipolar field results added, equations complete.
- [PDF] <a href="{{ 'assets/pdf/regular_tensors_polar_coordinates.pdf' | relative_url }}">Regularity conditions for general tensors in polar coordinates</a>.
<br />
---

### Code and demos
- [Repo] [PlesioGeostroPy](https://github.com/GentleMin/PlesioGeostroPy).
- [Documentation] [PlesioGeostroPy](https://gentlemin.github.io/PlesioGeostroPy/).
- [IPython notebook] [Regularity conditions on tensor components in polar coordinates](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/demos/Demo_Regularity.ipynb).
- [IPython notebook] [Quickstart for PlesioGeostroPy](https://gentlemin.github.io/PlesioGeostroPy/demos/Demo_PlesioGeostroPy_Basics.html), alternatively view using [nbviewer](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/demos/Demo_PlesioGeostroPy_Basics.ipynb). Further code-specific tutorials, please refer to the documentation page.
- [IPython notebook] [Eigenvalue solver for PG model](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/Eigen_Solve.ipynb).
- [IPython notebook] [Demonstrative tests](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/Tests.ipynb), currently includes
  - Using recurrence relation for evaluation of Jacobi polynomials,
  - Using product form to calculate the inner product matrices,
  - Multi-precision libraries, precision and efficiency tests, and calculating matrices in multi-prec,
  - Basis functions for vorticity and velocity components.
