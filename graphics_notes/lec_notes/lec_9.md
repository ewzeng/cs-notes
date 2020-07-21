geometry processing on meshes: upsampling via interpolation, downsampling, regularization

today: how to rep meshes (data structures), process meshes (geo processing)

#### mesh rep

some goals: constant time access to neighbors (e.g. surface normal calculation), easy editing geometry

if mesh is manifold: many nice properties like edge connects two faces, Euler's formula etc. so always assume we are working with manifolds (or MwB)

also assume manifold orientable: each triangle on same surface has same winding rule

triangle-neighbor: store a list of vertices. triangle = indices of vertices + neighbor triangle pointers. each vertex has a pointer to a triangle it is part of.

half edge (a directed edge): stores pointers to twin, next, vertex (where it ends), edge, face (to the left)

- use twin and next pointers to move around mesh (note orientation important!)
- what we will use from now on

#### local mesh operations

basic ops: flip, split, collapse edges (require careful pointer reassignments, may add/delete elements)

#### global mesh operations

loop subdivision:

- C2; approximation, not interpolation