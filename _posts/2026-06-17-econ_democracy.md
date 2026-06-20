---
layout: post
title: Optimizing society 2 - Democracy of homo economicus
date: 2026-06-17 22:12:00-0400
description: Ideal, too ideal, or not so ideal? 
categories: Culture
cjk: false
giscus_comments: true
related_posts: true
---

We have already derived that when optimizing a global utility function that is an equal summation of individual's utilities, the simplest iteration scheme based on gradient descent / steepest descent takes the form

$$
\mathbf{x}^{t+1} = \mathbf{x}^t + \alpha \sum_i \nabla u_i(\mathbf{x}^t).
$$

This formulation exhibits several properties. First, the gradient is an equal summation of each individual's gradient - everyone contributing to the total utility receives equal consideration, ideally with *direct democracy*. Second, the contribution from each individual faithfully reflects the direction in which their own utility / happiness rises the fastest, and the magnitude of their contribution to the total gradient is proportional to their utility increase in the said direction. In a society, the first property indicates a democratic social ruling. The second property indicates that each individual is rational (true representation of the utility) and narrowly self-interested (strives to raise their own utility). Therefore we may conclude that the scheme is, in fact, closest to a democracy of *homo economicus*.

The duality of gradient descent with $$U=\sum_i u_i$$ and a democracy of the idealised homo economicus extends to their properties in application. Gradient descent is often a robust and "cheap" choice of optimization, requiring minimal memory and computational cost per iteration (among derivative-based methods; one could of course achieve lower cost with gradient-free methods such as *simplex method*, some *evolutionary algorithms*, etc.). It also has guaranteed convergence property on convex objective functions, given that the step size $$\alpha$$ is adequately small. Therefore it is often the *safe* and conservative option if one has no further prior information of the optimization problem.

Such properties might be transferred to the democracy of economic men. Such democracy would require only a small amount of effort to organize (consider also how a free market is sometimes described to be *efficient* in promoting utilities). With the mathematical model in mind, one can also conclude that democracy of economic men would exhibit guaranteed convergence given that the global utility is convex, and given the step size, i.e. the pace at which the society is evolving, is sufficiently small. Thus one might argue that such democracy is indeed an ***ideal*** solution.

Except gradient descent is not ideal at all - anyone working with data science, machine learning, optimization and inverse problems would know better. To begin with, behaviour of the algorithm is quite sensitive to the step size of choice, even on simple quadratic optimization problems. Choose a larger step size, and you may overshoot beyond the minimum in the direction of gradient (Fig. 1), creating zig-zag patterns in the parameter space (Fig. 2). In extreme cases, large step sizes can also lead to divergence. On the other hand, going towards the conservative side and choosing small step size can result in painfully slow convergence.

The problem with gradient descent is even more severe with non-convex optimizations. It might get stuck at saddle points or suboptimal local minima, refusing to make further progress to optimization. The fact that vanilla gradient descent is far from ideal is the main motivation behind a century of optimization theory and algorithm design.


<div class="row justify-content-center">
    <div class="col-sm-12">
        {% include figure.html path="assets/img/TNN2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Figure 1. Effect of step size on gradient descent - example in 1D optimization. Credit: Subir Varma and Sanjiv Das, <a href="https://srdas.github.io/DLBook/GradientDescentTechniques.html">Deep Learning, 2018</a>.
</div>


The same can be said for the democracy of homo economicus. Even in simple situations, where we assume that the happiness of different individuals more or less form a continuum and align to form a convex global utility function, such democracy is sensitive to the evolution speed. Evolving too fast and radically, the society would take too many detours (zig-zag) and even deteriorate in its members' collective happiness (divergence). Evolving too slow and conservatively, the progress might be so slow that the society is unable to cope with the upcoming external challenges, including threats from other civilisations, environmental change, etc. Essentially all extinction is due to slow evolution (the latter), where the species are unable to keep up with and adapt to the changing surroundings.


<div class="row justify-content-center">
    <div class="col-sm-12">
        {% include figure.html path="assets/img/gd_zigzag.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Figure 2. Zig-zag pattern of gradient descent with large step size in 2D optimization problems. Credit: Just Another Tech Blogger, <a href="https://medium.com/@amitkhanna_4249/taming-the-loss-landscape-how-gradient-updates-guide-deep-learning-26f565199f43">Eigenvectors as The Compass Of Gradient Updates in Deep Learning, 2025</a>.
</div>


On the other hand, there is no guarantee that our social utility is convex to begin with. Even if individual utility is convex, social stratification would create social classes or groups, leading to multiple clusters of individuals whose interest somewhat align among themselves (in some aspects), but whose combined interest is misaligned with those of other clusters. In addition, the individual happiness need not be a convex function of the social status vector $$\mathbf{x}$$. For instance, one might be happy living in a lively populous region, less happy in a small town, but become happy again in the countryside where the nature is within close reach. In this case, the utility as a function of population density would have multiple peaks. Whether due to non-convex feature of individual utility function or the combined effects, the global utility is most likely highly multi-modal and full of local optima. A democracy of homo economicus would then most likely be inefficient in improving the utility of the society. An idealised model might not be so ideal after all.
