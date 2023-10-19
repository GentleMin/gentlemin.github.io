---
layout: page
title: Plesio-Geostrophy Model
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
- Theory and concept paper, [Jackson and Maffei (2020)](https://www.research-collection.ethz.ch/handle/20.500.11850/509840).
- Daria Holdenried-Chernoff's [doctoral thesis (2021)](https://www.research-collection.ethz.ch/handle/20.500.11850/509840).
<br />

---

### Formulation and documentation
- [PDF] <a href="{{ 'assets/pdf/Ingredients.pdf' | relative_url }}">Formulations for PG model: missing ingredients and new recipes</a>.
- [PDF] <a href="{{ 'assets/pdf/regular_tensors_polar_coordinates.pdf' | relative_url }}">Regularity conditions for general tensors in polar coordinates</a>.
<br />

---

### Code and demos
- [Repo] [PlesioGeostroPy](https://github.com/GentleMin/PlesioGeostroPy).
- [IPython notebook] [Demo and Tutorial for PlesioGeostroPy](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/PG_demo.ipynb).
- [IPython Notebook] [Eigenvalue solver for PG model](https://nbviewer.org/github/GentleMin/PlesioGeostroPy/blob/main/EigenPG.ipynb).

