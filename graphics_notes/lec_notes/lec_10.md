#### mesh upsampling (subdivision)

loop subdivision alg: split each triangle into four, then adjust vertex positions according to weights. not hard to implement with the half-edge data structure.

- each vertex degree 6 $\rightarrow$ "regular-looking". however, if mesh top equiv to sphere, not all vertices can have degree 6. thus exist a few "extraordinary" points. can only guarantee $C^1$ at extraordinary points.

catmull-clark subdivison alg: add face points, then edge points, then adjust old vertices, then connect. repeat.

- every iteration creates quad meshes. same continuity results as loob subdiv.

how do we do sharp creases? label vertices as "sharp" and use slightly different subdivision rules. (can handle boundary edges the same way)

#### mesh downsampling (simplification)

goal: reduce number of mesh elements while maintaining overall shape

one way: estimate error from collapsing an edge. iteratively collaspe edges with smallest error (greedy alg).

- quadric error (can be computed fast with quadric sym matrices)

#### mesh regularization

regularization can be achieved by recursive positioning techniques

"regular-looking" defined by a few rules of thumb