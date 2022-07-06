---
layout: post
author: Nate Hofmann
---

This post is a series of visual demonstrations of what Voronoi relaxation looks like under varying distance functions and alternative formulations. The code behind the diagrams and relaxation algorithm are form a [small C program I wrote](https://github.com/njhofmann/voronoi-generation), Python was used to process and visualize the results.

## Background

(**Note:** this is a simplification of the proper definition of Voronoi diagrams and relaxation)

[Voronoi diagrams](https://en.wikipedia.org/wiki/Voronoi_diagram) are commonly introduced as a set of $n$ points $X=\{x_1,x_2,...,x_n\}\in \mathbf{R}^k$ where each point $x_i$ is apart of some "cell" $R_j$. Each $R_j$ is said to have some "center" point $c_{R_j}$ such that every point $\in R_j$ is closer to $c_{R_j}$ than the center point of any other cell $c_{R_i}$, according to some [distance metric](https://en.wikipedia.org/wiki/Metric_(mathematics)) $D$.

From this, we introduce [Voronoi relaxation](https://en.wikipedia.org/wiki/Lloyd%27s_algorithm) as the process of finding Voronoi diagrams where every cell has roughly the same "area" (in this project we work with discrete points, so we define area as number of points in a cell). This is done by selecting a subset of $t$ points $c\in X$ and designating as **center points**. We then iteratively repeat:

1. Find the Vornoi diagram of the $t$ center points by, for each point $x_i\in X$, finding which center point it is closest to (as defined by $D$) and adding it to that center's cell. For example, if $x_i$ is closest to center $c_j$, we add it to the cell $R_j$. We can then define $R_j$ as the set of points whose closest center point was $c_j$.

2. Next, we define a new set of $t$ center points by finding the a new for of each cell $R_i$. In this project, this is the cell's **centroid** - or arithmetic mean of each point $x_i\in R_j$.

These two steps are usually repeated either for a fixed number of steps, or until convergence has occured. The latter occurs when each cell is roughly the same size (as defined by the number of pixels in the cell), commonly identified when the distance between two successive centers of the same cell are less than some threshold $\tau$ (usually something .1).

## Distance Functions

The most common distance metrics selected for $D$ are [Euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance) and [Manhattan distance](https://en.wikipedia.org/wiki/Taxicab_geometry), but there also exist other distance metrics for points in $\mathbf{R}^k$ that might be used.

In explaining the [distance metrics](https://en.wikipedia.org/wiki/Metric_(mathematics)) explored in this piece below, we say $x$ and $y$ are two points in $R^k$ whose distance is being measured by distance metric $D$.

Many more distance functions exist, but only a few are demonstrated below out in the interest of brevity and keeping the visualizations interesting (some devolve into garbage non-sense).

To demonstrate each distance function, we demonstate Voronoi relaxation in 2D and 3D space - as well as how those centers change position over time. For the Minowski and Yang metrics - for $p$ values of 3, 4, and 5 are demonstrated.

For 2D ($R^2$ space), gifs show Voronoi relaxation for 100 iterations occuring on a 300x300 plane under each distance metric, starting from 32 randomly selected centers.

For 3D ($R^3$), images show the resulting Vornoi diagram after 100 iterations of Voronoi relaxation on a 300x300x300 sapce under each distance metric, starting from 32 randomly selected centers.

### [Bray-Curtis](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.braycurtis.html#scipy.spatial.distance.braycurtis)

While technically not a distance function due to not obeying the triangle inequality, it comes from biostatistics   aiming to measure the how different two "sites" are on a per-element basis. Guaranteed to be betwee $[0,1]$ if all elements are positive.

$$D(x,y)=\frac{\sum\limits_{i=1}^k |x_i-y_i|}{\sum\limits_{i=1}^k |x_i+y_i|}$$

{:style="text-align:center;"}![yay](/assets/voronoi/2d-canberra.gif)

<div align="center">
    ![yay](/assets/voronoi/2d-canberra.gif)
</div>

### [Canberra](https://en.wikipedia.org/wiki/Canberra_distance)

A weighted version of Manhanttan distance that weights the $i$-th element by the sum of asboluste $x_i$ and absolute $y_i$.

$$D(x,y)=\sum\limits_{i=1}^k \frac{|x_i - y_i|}{|x_i| + |y_i|}$$

### [Chebyshev](https://en.wikipedia.org/wiki/Chebyshev_distance)

Also known as the maximum metric, defines $D(x,y)$ as the maximum distance between an two of their coordinate pairs ($x_1$ and $y_1$, $x_2$ and $y_2$, etc.).

$$D(x,y)=\max\limits_i (|x_i - y_i|)$$

### [Hellinger](https://en.wikipedia.org/wiki/Hellinger_distance#Discrete_distributions)

$$D(x,y)=\frac{1}{\sqrt{2}}\sqrt{\sum\limits_{i=1}^k (\sqrt{x_i} - \sqrt{y_i})^2}$$

### [Minkowski](https://en.wikipedia.org/wiki/Minkowski_distance)

Basically a generalization of the Manhattan and Euclidian distances. Measures distances on normed vector spaces, generalized by integer $p > 0$.

$$D(x,y)=(\sum\limits_{i=1}^k |x_i - y_i|^p)^\frac{1}{p} $$

### [Yang](https://link.springer.com/article/10.1007/s10618-019-00622-6)

A "newer" distance metric introduced for the purposes of retaining all the properties of distance metrics while being more useful than similarity measures used in high dimensional data (like cosine "distance").

$$D(x,y)=((\sum\limits_{i:x_i\geq y_i} x_i - y_i)^p + (\sum\limits_{i:x_i < y_i} y_i - x_i)^p)^\frac{1}{p}$$

## Alternative Formulations

There exist several modifications to the original definitions of Voronoi diagrams and relaxation that lead to some interesting visual phenonena. 

Perhaps  one of the simplest, but still compelling, are **k-th order** Voronoi diagrams. Here instead of assigning pixels to cells based on which center they are closest to, they are assigned to cells based on their 2-nd closest center, 3-rd closest, and so on ending at the $t$-th closest center. This last being this is equivalent to assigning based on furthest center. Formally we may also say, assigning based on the closest center (the original definition) is a *1-st order* Vorinoi diagram.

## Visualizations

Here we demonstrate Voronoi relaxation occuring under a variety of conditions.

For the Minowski and Yang metrics, several values of $p>2$ are demonstrated. 

### 2D

Here gifs show Voronoi relaxation for 100 iterations occurs on a 300x300 2D plane under each distance metric, starting from 32 randomly selected centers.

For the Minowski and Yang metrics, several values of $p$ are given.

#### Canberra

#### Chebyshev

#### Euclidian

#### Manhattan

#### Minkowski-3

#### Minkowski-4

#### Yang-3

#### Yang-4

### 3D



#### Canberra

#### Chebyshev

#### Euclidian

#### Manhattan

#### Minkowski-3

#### Minkowski-4

#### Yang-3

#### Yang-4

 TODo higher order
 TODO centers moving
 TODO merge into equation, 2d gif, 3d img



