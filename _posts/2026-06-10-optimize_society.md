---
layout: post
title: Optimizing society
date: 2026-06-10 22:12:00-0400
description: Evolution of society as an optimization process
categories: Culture
cjk: false
giscus_comments: true
related_posts: true
---

There are certainly many aspects of society that are linked with optimization. Every entity participating in economics supposedly maximizes their utilities. Traders try to optimize their profits; buyers try to minimize their costs; asset managers try to maximize the outcome of their investments. Yet I always believe that the link between society and optimization goes even beyond all these - not only micro decisions made by entities in the economy can be described by an optimization problem, but the entire evolution of the society as well.

It is not uncommon to see optimization algorithms inspired by the society or biological groups. For instance, the Evolution Strategy (ES), or more generally Evolutionary Algorithms (EA), are inspired by the idea of biological evolution, and achieve the purpose of optimization by generating progressive more optimal samples at every iteration / generation. Transplanting the idea in social evolution into optimization problem reveals the following belief: we think that a society, whether a human society, or a biological population, or perhaps a biome, should be optimizing some objective as it evolves through time. If this is indeed the case, then we can also exploit this belief further by actually casting the evolution of society as an optimization problem.

<br />

## The optimization problem

Think about the status of the society, i.e. all the properties / parameters one needs to describe a society, and encode them in the vector $$\mathbf{x}$$. These parameters comprise everything society related, from technology to politics, from culture to law. Within this vector lies an enormous amount of information. Everything from issues as big as the yearly economic output, the values of each industry; how often people vote in a society, and how many people vote; to issues as small as how many people visited a bakery today, and how well the kiosk around the corner has been doing lately. Information as tangible as the properties and specifications of the newly released smartphone, and information as intangible as people's attitude towards elderly, to what extent children are responsible for supporting their retired parents, and to what extent people rely on personal connections or nepotism in terms of career, health care, etc. One can only imagine that the state vector $$\mathbf{x}$$ must be living in an extremely high-dimensional space $$\mathcal{X}$$; considering it should also encode intangible cultural properties, it is highly likely that $$\mathcal{X}$$ actually needs to be infinite dimensional. This vector, describing the status of the society, will be the parameter to be optimized on.

The objective function to optimize is then a function of the high-dimensional vector $$\mathbf{x}$$. What goes in the objective function? Naturally, one would think of the utility function used in economics as a measure for individual satisfaction - in a utilitarianism sense, what to maximize if not one's satisfaction? Let's denote these utility functions as 

$$
u_i: \mathcal{X} \mapsto \mathbb{R}
$$

for individual indexed $$i=1,2,3\cdots$$. Now the objective of the society may be considered as optimizing the sum of individual utility functions (debatable). Individual utiliity functions may typically be localised, in the sense that it is typically most sensitive to system parameters concerning the individual or surrounding the individual; however, in a non-selfish sense, this function can of course depend on the well-being, state, and happiness of others, as well as aspects of the society that do not directly affect the said individual. In this sense, we may also define the individual utility functions as implicit functions satisfying equations

$$
\begin{aligned}
u_1 &= f_1(\mathbf{x}, u_1(\mathbf{x}), \cdots u_N(\mathbf{x})), \\
u_2 &= f_2(\mathbf{x}, u_1(\mathbf{x}), \cdots u_N(\mathbf{x})), \\
&\vdots \\
u_N &= f_N(\mathbf{x}, u_1(\mathbf{x}), \cdots u_N(\mathbf{x})),
\end{aligned}
$$

where $$N$$ is the total number of individuals considered, and $$f_i$$ describes explicitly how the utility of the $$i$$-th individual depends on the parameters as well as other people's utilities. Nevertheless we assume that these implicit functions exist and take the form $$u_i(\mathbf{x})$$. We hence introduce this social utility function as 

$$
\mathcal{U}(\mathbf{x}) = \sum_i u_i(\mathbf{x})
$$

If we think of social evolution as an optimization problem, it shall then take the form

$$
\max_{\mathbf{x}} \mathcal{U}(\mathbf{x}) = \max_{\mathbf{x}} \sum_i u_i(\mathbf{x})
$$

or in a more canonical form

$$
\min_{\mathbf{x}} \mathcal{L}(\mathbf{x}).
$$

Here I defined the cost function as negative utility $$\mathcal{L}(\mathbf{x}) = - \mathcal{U}(\mathbf{x}) = -\sum_i u_i(\mathbf{x})$$. One can of course also define it as the negative of any monotonically increasing function of the utility, e.g. $$\mathcal{L}(\mathbf{x}) = -\log \mathcal{U}(\mathbf{x})$$, provided utility function is non-negative, but all these fancy transforms won't be useful unless there is a deeper interpretation of such quantities.



## From optimization to dynamical system

The optimization perspective is "static" - it merely describes an objective to optimize. An alternative perspective is describing the evolution of the society as a dynamical system of the social state vector $$\mathbf{x}$$, in the form of

$$
\mathbf{x}^{t+1} = f\left(\mathbf{x}^{t}\right).
$$

Although one is static and one is dynamic, these two perspectives are not mutually exclusive.
In fact, the optimization problem, in combination with *rules for social evolution*, naturally induces a dynamical system.
This conversion from the optimization problem to the discrete map is realized by devising an optimization process, or in a more concrete sense, an optimization algorithm. For instance, using the gradient descent algorithm, the optimization problem yields the dynamical system

$$
\begin{aligned}
\mathbf{x}^{t+1} &= \mathbf{x}^t - \alpha \nabla \mathcal{L}(\mathbf{x}^t) \\
&= \mathbf{x}^t + \alpha \nabla \mathcal{U}(\mathbf{x}^t) \\
\mathbf{x}^{t+1} &= \mathbf{x}^t + \alpha \sum_i \nabla u_i(\mathbf{x}^t)
\end{aligned}
$$

where $$\alpha$$ is the step size. Under such rules, the evolution of any social parameter $$x_j$$ will then be in the direction that most efficiently increases the overall utility gain $$\delta \mathcal{U} = \sum_i \delta u_i$$, with a step size $$\alpha$$.

Let us talk a bit more about the *rules for social evolution*. In the mathematical formulation, it would refer to how the social state vector is modified at each iteration. In reality, such modification is achieved via various socio-political activities: posting personal views online, protesting in the streets, and in aggregate shifting the collective opinion of the society; voting for representatives or submitting legislative drafts or proposals, hence affecting the political functions directly or indirectly; participating in a revolution, aiming at establishing a new political regime... These activities constitute the *rules*, and determines the iteration scheme of the optimization problem.

