### Lecture 2

rasterize: image $\rightarrow$ pixels.

problem: what is the set of pixels approximating a triangle?

solution: sampling. check if center of each pixel inside triangle.

how to tell if point $P$ inside triangle? three line test

- extend the sides into lines. check if $P$ is in the correct side of each line.
- to do this, for each line, do a dot product with the perp line and then check sign.

edge case: if sample point on edge, include if edge is top edge or left edge.

modern point-in-triangle tests use parallelism + sampling.

problem with sampling: jaggy edges due to pixelation.

### Lecture 3

aliasing: artifacts due to sampling (e.g. jaggy edges). alias = "false identity."

frequency alias: two frequencies indistinguishable at a sampling rate.

- one way to avoid - sample faster at high frequencies. 
  - nyquist theorem. (no aliasing if less than half the sampling frequency.)
- or can filter images to get rid of high frequencies.
  - filters! fourier analysis comes into play.

anti-aliasing of triangles: pixels take intermediate values (avoid jaggies).

- one way to do it: use a 1-pixel filter to blur the edges (result is same as taking the average over a pixel b/c filters are convolutions)
- or supersampling (sample multiple points in a pixel and average the values). lots of theory here. or average an adjacent group of pixels.

### Lecture 4

transform = function acting on points (e.g. rotation, translation, scaling).

clearly important in making movies and stuff.

transformations represented as matrices.

- to make translation work in 2D, add an auxiliary third coordinate. (in fact, all affine maps can be done like so. this is called homogenous coordinates.)