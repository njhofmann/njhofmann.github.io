---
layout: post
author: Nate Hofmann
---

[Voronoi diagrams](https://en.wikipedia.org/wiki/Voronoi_diagram) are commonly introduced as a set of points $x_1,x_2,...,x_k\in \mathbf{R}^k$ where each point $x_i$ apart of some "cell" $R_j$, where each $R_j$ has some "center" point $x_{R_j}$ such that every point $\in R_j$ is closer to $x_j$, according to some [distance metric](https://en.wikipedia.org/wiki/Metric_(mathematics)) $D$, than the center of any other cell $R_g$.

(**Note:** this is a gross simplification of the proper definition of Voronoi diagrams)

From this, we say that [Voronoi relaxation](https://en.wikipedia.org/wiki/Lloyd%27s_algorithm) is the process of finding Voronoi diagrams where each cell is roughly equal in its "area" (the number of points in that cell. This is done by ...

When creating Voronoi diagrams, for the distance metric $D$ you will most often see [Euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance) and [Manhattan distance](https://en.wikipedia.org/wiki/Taxicab_geometry). Yet there are a variety of other distance metrics for points in $mathbf{R}^k$ that could be used such as ...

This post is a demonstration of what Voronoi relaxation looks like under less-common distance metrics, using visualizations of 2D diagrams using a [small C program I wrote](https://github.com/njhofmann/voronoi-generation) (check it out!).

## Distance Functions

### Observations 

## Runtime Analysis

f