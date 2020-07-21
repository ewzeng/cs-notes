rasterization: turn stuff into pixels

frame buffer: 2D array of pixels ready to be projected onto the screen (output of rasterization)

how to describe geometry (before rasterization):

- a sequence of vertices + a openGL command (e.g. GL_trianges, or GL_points, or some other shape primitive)

graphics pipline: abstract drawing machine (send openGL commands, see above, and get a frame buffer)

- rasterization is part of the pipeline

today: rasterizing triangles; many advantages

what pixel values approximate a triangle? one way: sampling (core idea in graphics). sample if each pixel center is inside triangle.

how to tell if point inside a triangle?

- check if point is in the correct half planes (take dot product with perp)
- edge cases: top/left edge part of the triangle

can speed up sampling with parallelism

a problem: jaggies
