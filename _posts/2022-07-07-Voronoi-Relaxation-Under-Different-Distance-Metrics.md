---
layout: post
author: Nate Hofmann
use_math: true
---

This post is a series of visual demonstrations of what Voronoi relaxation looks like under varying distance functions and alternative formulations. The code behind the diagrams and relaxation algorithm are from a [small and dreadfully simple C program I wrote](https://github.com/njhofmann/voronoi-generation), Python was used to process and visualize the results.

If you have any questions, suggestions, or comments about this post, feel free to contact me via the contact info on my home page!

## Background

(**Note:** this is a simplification of the proper definition of Voronoi diagrams and relaxation)

[Voronoi diagrams](https://en.wikipedia.org/wiki/Voronoi_diagram) are commonly introduced as a set of $n$ points $X=\{x_1,x_2,...,x_n\}\in \mathbf{R}^k$ where each point $x_i$ is apart of some "cell" $R_j$. Each $R_j$ is said to have some "center" point $c_{R_j}$ such that every point $\in R_j$ is closer to $c_{R_j}$ than the center point of any other cell $c_{R_i}$, as measured by some [distance metric](https://en.wikipedia.org/wiki/Metric_(mathematics)) $D$. 

From this, we introduce [Voronoi relaxation](https://en.wikipedia.org/wiki/Lloyd%27s_algorithm) as the process of finding Voronoi diagrams where every cell has roughly the same "area" (in this project we work with discrete points, so we define area as number of points in a cell). This is done by selecting a subset of $t$ points $c\in X$, and designating them as **center points**. We then iteratively repeat:

1. Find the Vornoi diagram of the $t$ center points by - for each point $x_i\in X$, finding its closest center point (as defined by $D$) and adding it to that center's cell. For example, if $x_i$ is closest to center $c_j$, we add it to the cell $R_j$. We can then define $R_j$ as the set of points whose closest center point was $c_j$.

2. Next, we define a new set of $t$ center points by finding a new center for each cell $R_i$. In this project, this we define this as the cell's **centroid** - or the arithmetic mean of each point $x_i\in R_j$.

These two steps are usually repeated either for a fixed number of steps, or until convergence has occured. The latter occurs when each cell is roughly the same size (as defined by the number of pixels in the cell), commonly identified when the distance between two successive centers of the same cell are less than some threshold $\tau$ (usually something like .1).

## Distance Functions

The most common distance metrics selected for $D$ are [Euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance) and [Manhattan distance](https://en.wikipedia.org/wiki/Taxicab_geometry), but there also exist other distance metrics for points in $\mathbf{R}^k$ that might be used.

In explaining the [distance metrics](https://en.wikipedia.org/wiki/Metric_(mathematics)) explored in this piece below, we say $x$ and $y$ are two points in $R^k$ whose distance is being measured by distance metric $D$.

Many more distance functions exist, but only a few are demonstrated below in the interest of brevity and keeping the visualizations interesting (some devolve into garbage non-sense).

To demonstrate each distance function, we demonstate Voronoi relaxation in 2D and 3D space - as well as how those centers change position over time. For the Minowski and Yang metrics - for $p$ values of 3, 4, and 5 are demonstrated. Each cell is assigned a distinct color.

For 2D ($R^2$ space), GIFs show Voronoi relaxation for 100 iterations occuring on a 300x300 plane under each distance metric, starting from 32 randomly selected centers.

For 3D ($R^3$), images show the resulting Vornoi diagram after 100 iterations of Voronoi relaxation on a 100x100x100 space under each distance metric, starting from 32 randomly selected centers.

### [Euclidean](https://en.wikipedia.org/wiki/Euclidean_distance)

The most common distance function used with Voronoi diagrams (and in general), gives the length of the line between $x$ and $y$.

\$\$D(x,y)=\sqrt{\sum\limits_{i=1}^k (x_i-y_i)^2}\$\$

<script type="math/tex; mode=display">D(x,y)=\sqrt{\sum\limits_{i=1}^k (x_i-y_i)^2}</script>

<center><img src="assets/voronoi/euclidean/2d-euclidean-cells.gif"></center>
<center>Euclidean in 2D</center>

<center><img src="assets/voronoi/euclidean/2d-euclidean-centers.gif"></center>
<center>Cell centers over time in Euclidean-2D</center>

<center><img src="assets/voronoi/euclidean/3d-euclidean-cells.jpg"></center>
<center>Euclidean in 3D</center>

<center><img src="assets/voronoi/euclidean/3d-euclidean-centers.jpg"></center>
<center>Cell centers over time in Euclidean-3D</center>

### [Manhattan](https://en.wikipedia.org/wiki/Taxicab_geometry)

Probably the second most common distance function "in general", giving the sum of the absolute differences between the corresponding elements of $x$ and $y$.

$$D(x,y)=\sum\limits_{i=1}^k |x_i-y_i|$$

<center><img src="assets/voronoi/manhattan/2d-manhattan-cells.gif"></center>
<center>Manhattan in 2D</center>

<center><img src="assets/voronoi/manhattan/2d-manhattan-centers.gif"></center>
<center>Cell centers over time in Manhattan-2D</center>

<center><img src="assets/voronoi/manhattan/3d-manhattan-cells.jpg"></center>
<center>Manhattan in 3D</center>

<center><img src="assets/voronoi/manhattan/3d-manhattan-centers.jpg"></center>
<center>Cell centers over time in Manhattan-3D</center>

### [Bray-Curtis](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.braycurtis.html#scipy.spatial.distance.braycurtis) / Sorenborg

While technically not a distance function due to not obeying the triangle inequality, it comes from biostatistics and related fields aiming to measure the how different two "sites" (says sites of animals). are on a per-element basis. Guaranteed to be between $[0,1]$ if all elements are positive.

$$D(x,y)=\frac{\sum\limits_{i=1}^k |x_i-y_i|}{\sum\limits_{i=1}^k |x_i+y_i|}$$

<center><img src="assets/voronoi/bray-curtis/2d-bray-curtis-cells.gif"></center>
<center>Bray-Curtis in 2D</center>

<center><img src="assets/voronoi/bray-curtis/2d-bray-curtis-centers.gif"></center>
<center>Cell centers over time in Bray-Curtis-2D</center>

<center><img src="assets/voronoi/bray-curtis/3d-bray-curtis-cells.jpg"></center>
<center>Bray-Curtis in 3D</center>

<center><img src="assets/voronoi/bray-curtis/3d-bray-curtis-centers.jpg"></center>
<center>Cell centers over time in Bray-Curtis-3D</center>

### [Canberra](https://en.wikipedia.org/wiki/Canberra_distance)

A weighted version of Manhanttan distance, where the $i$-th element is weighted by the sum of the absolute value of $x_i$ and absolute value of $y_i$.

$$
D(x,y)=\sum\limits_{i=1}^k \frac{|x_i - y_i|}{|x_i| + |y_i|}
$$

<center><img src="assets/voronoi/canberra/2d-canberra-cells.gif"></center>
<center>Canberra in 2D</center>

<center><img src="assets/voronoi/canberra/2d-canberra-centers.gif"></center>
<center>Cell centers over time in Canberra-2D</center>

<center><img src="assets/voronoi/canberra/3d-canberra-cells.jpg"></center>
<center>Canberra in 3D</center>

<center><img src="assets/voronoi/canberra/3d-canberra-centers.jpg"></center>
<center>Cell centers over time in Canberra-3D</center>

### [Chebyshev](https://en.wikipedia.org/wiki/Chebyshev_distance)

Also known as the maximum metric, defines distance as the maximum distance between any two of their corresponding elements of $x$ and $y$ ($x_1$ and $y_1$, $x_2$ and $y_2$, etc.).

$$D(x,y)=\max\limits_i (|x_i - y_i|)$$

<center><img src="assets/voronoi/chebyshev/2d-chebyshev-cells.gif"></center>
<center>Chebyshev in 2D</center>

<center><img src="assets/voronoi/chebyshev/2d-chebyshev-centers.gif"></center>
<center>Cell centers over time in Chebyshev-2D</center>

<center><img src="assets/voronoi/chebyshev/3d-chebyshev-cells.jpg"></center>
<center>Chebyshev in 3D</center>

<center><img src="assets/voronoi/chebyshev/3d-chebyshev-centers.jpg"></center>
<center>Cell centers over time in Chebyshev-3D</center>

### [Hellinger](https://en.wikipedia.org/wiki/Hellinger_distance#Discrete_distributions)

Basically the Euclidean norm between the difference of the square root vectors of $x$ and $y$, more formally a version of a probability distribution similarity measure assuming $x$ and $y$ are discrete distributions. 

$$D(x,y)=\frac{1}{\sqrt{2}}\sqrt{\sum\limits_{i=1}^k (\sqrt{x_i} - \sqrt{y_i})^2}$$

<center><img src="assets/voronoi/hellinger/2d-hellinger-cells.gif"></center>
<center>Hellinger in 2D</center>

<center><img src="assets/voronoi/hellinger/2d-hellinger-centers.gif"></center>
<center>Cell centers over time in Hellinger-2D</center>

<center><img src="assets/voronoi/hellinger/3d-hellinger-cells.jpg"></center>
<center>Hellinger in 3D</center>

<center><img src="assets/voronoi/hellinger/3d-hellinger-centers.jpg"></center>
<center>Cell centers over time in Hellinger-3D</center>

### [Minkowski](https://en.wikipedia.org/wiki/Minkowski_distance)

A generalization of the Manhattan and Euclidian distances by integer $p > 0$ ($p=1$ is Manhattan distance, $p=2$ is Euclidean). Measures distances on normed vector spaces.

$$D(x,y)=(\sum\limits_{i=1}^k |x_i - y_i|^p)^\frac{1}{p}$$

#### When $p=3$

<center><img src="assets/voronoi/minkowski/2d-minkowski-cells-3.gif"></center>
<center>Mikowski-3 in 2D</center>

<center><img src="assets/voronoi/minkowski/2d-minkowski-centers-3.gif"></center>
<center>Cell centers over time in Mikowski-3-2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-cells-3.jpg"></center>
<center>Minkowski-3 in 2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-centers-3.jpg"></center>
<center>Cell centers over time in Minkowski-3-2D</center>

#### When $p=4$

<center><img src="assets/voronoi/minkowski/2d-minkowski-cells-4.gif"></center>
<center>Minkowski-4 in 2D</center>

<center><img src="assets/voronoi/minkowski/2d-minkowski-centers-4.gif"></center>
<center>Cell centers over time in Minkowski-4-2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-cells-4.jpg"></center>
<center>Minkowski-4 in 2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-centers-4.jpg"></center>
<center>Cell centers over time in Minkowski-4-2D</center>

#### When $p=5$

<center><img src="assets/voronoi/minkowski/2d-minkowski-cells-5.gif"></center>
<center>Minkowski-5 in 2D</center>

<center><img src="assets/voronoi/minkowski/2d-minkowski-centers-5.gif"></center>
<center>Cell centers over time in Minkowski-5-2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-cells-5.jpg"></center>
<center>Minkowski-5 in 2D</center>

<center><img src="assets/voronoi/minkowski/3d-minkowski-centers-5.jpg"></center>
<center>Cell centers over time in Minkowski-5-2D</center>

### [Yang](https://link.springer.com/article/10.1007/s10618-019-00622-6)

A "newer" distance metric introduced for the purposes of retaining all the properties of distance metrics while being more useful than similarity measures used in high dimensional data (like cosine "distance").

$$D(x,y)=((\sum\limits_{i:x_i\geq y_i} x_i - y_i)^p + (\sum\limits_{i:x_i < y_i} y_i - x_i)^p)^\frac{1}{p}$$

#### When $p=3$

<center><img src="assets/voronoi/yang/2d-yang-cells-3.gif"></center>
<center>Yang-3 in 2D</center>

<center><img src="assets/voronoi/yang/2d-yang-centers-3.gif"></center>
<center>Cell centers over time in Yang-3-2D</center>

<center><img src="assets/voronoi/yang/3d-yang-cells-3.jpg"></center>
<center>Yang-3 in 2D</center>

<center><img src="assets/voronoi/yang/3d-yang-centers-3.jpg"></center>
<center>Cell centers over time in Yang-3-2D</center>

#### When $p=4$

<center><img src="assets/voronoi/yang/2d-yang-cells-4.gif"></center>
<center>Yang-4 in 2D</center>

<center><img src="assets/voronoi/yang/2d-yang-centers-4.gif"></center>
<center>Cell centers over time in Yang-4-2D</center>

<center><img src="assets/voronoi/yang/3d-yang-cells-4.jpg"></center>
<center>Yang-4 in 2D</center>

<center><img src="assets/voronoi/yang/3d-yang-centers-4.jpg"></center>
<center>Cell centers over time in Yang-4-2D</center>

#### When $p=5$

<center><img src="assets/voronoi/yang/2d-yang-cells-5.gif"></center>
<center>Yang-5 in 2D</center>

<center><img src="assets/voronoi/yang/2d-yang-centers-5.gif"></center>
<center>Cell centers over time in Yang-5-2D</center>

<center><img src="assets/voronoi/yang/3d-yang-cells-5.jpg"></center>
<center>Yang-5 in 2D</center>

<center><img src="assets/voronoi/yang/3d-yang-centers-5.jpg"></center>
<center>Cell centers over time in Yang-5-2D</center>

## Alternative Formulations

There exist many modifications to the original definitions of Voronoi diagrams and relaxation that can also lead to some interesting visual phenonena. 

Perhaps one of the simplest modifications are **k-th order** Voronoi diagrams. Here instead of assigning points to cells based on their closest center, they are assigned to cells based on their 2-nd closest center, 3-rd closest, and so on ending at the $t$-th closest center (i.e. the furthest center). Formally we may also say, assigning based on the closest center (the original definition) is a *1-st order* Vorinoi diagram.

Below we show resulting image for each distance measure as before, under the same 2D formulation. We opt for images instead of gifs here because for $k>1$, cells tend to split apart into smaller groups resulting in less visually cohesive iterations.

### 1-st Order

#### Euclidean

<center><img src="assets/voronoi/euclidean/2d-euclidean-1st-order-cells.jpg"></center>

#### Manhattan

<center><img src="assets/voronoi/manhattan/2d-manhattan-1st-order-cells.jpg"></center>

#### Bray-Curtis

<center><img src="assets/voronoi/bray-curtis/2d-bray-curtis-1st-order-cells.jpg"></center>

#### Canberra

<center><img src="assets/voronoi/canberra/2d-canberra-1st-order-cells.jpg"></center>

#### Chebyshev

<center><img src="assets/voronoi/chebyshev/2d-chebyshev-1st-order-cells.jpg"></center>

#### Hellinger

<center><img src="assets/voronoi/hellinger/2d-hellinger-1st-order-cells.jpg"></center>

#### Minkowski

##### $p=3$

<center><img src="assets/voronoi/minkowski/2d-minkowski-3-1st-order-cells.jpg"></center>

##### $p=4$

<center><img src="assets/voronoi/minkowski/2d-minkowski-4-1st-order-cells.jpg"></center>

##### $p=5$

<center><img src="assets/voronoi/minkowski/2d-minkowski-5-1st-order-cells.jpg"></center>

#### Yang

##### $p=3$

<center><img src="assets/voronoi/yang/2d-yang-3-1st-order-cells.jpg"></center>

##### $p=4$

<center><img src="assets/voronoi/yang/2d-yang-4-1st-order-cells.jpg"></center>

##### $p=5$

<center><img src="assets/voronoi/yang/2d-yang-5-1st-order-cells.jpg"></center>
 
### -1-st Order

The $-1$-order occurs when points are added to cells based on the *furthest* center point. Generally the results under any distance formula are largely the same, only 2-4 cells emerge as most points have the same "furthest center point". 

Due to the aforementioned similarity across distace metrics, only the Euclidean and Manhattan distances are shown.

<center><img src="assets/voronoi/euclidean/2d-euclidean-furthest-cells.jpg"></center>
<center>Furthest cells in Euclidean-2D</center>

<center><img src="assets/voronoi/manhattan/2d-manhattan-furthest-cells.jpg"></center>
<center>Furthest cells in Manhattan-2D</center>
