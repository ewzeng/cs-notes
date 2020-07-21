#### raytracing intro

today: ray-tracing; we often trace light backwards (eye to source)

ray casting: cast one ray/pixel (alt to perspective projection), color according to intersection w/ geo + shading determined by tracing shadow rays

- recursive ray tracing: after hit, ray trace again (simulate bouncing light). calc shading of each hit via shadow rays, and avg everything

now: calc ray intersections

ray-mesh naive method: calc intersection with each triangle (solve ray and plane equation to get hit point, test if hit point inside triangle)

- many ways to optimize (moller trumbore algs)

ray-implicit surface method: plug ray into implicit surface equation; solve equation

- ray-sphere: solve for intersection, check discriminant

next time: want to acclerate ray-surface intersection calcs

#### accelerating raytracing

idea: bounding volume; ray intersection with axis-aligned box: fast, use slabs

uniform spatial grid: find bounding box, partition box into grid, note all geometry intersecting each cell, step thru cells in ray traversal order. need to be careful.

- bad for teapot in a stadium

non-uniform spatial partition. partition bbox unevenly. can use KD-tree: leaf nodes store list of objects. to ray-trace: do a top-down recursive in-order traversal ($t_{split}, t_{min}, t_{max}$)

- choosing split plane: can do median split; there are heuristics for max tree depth

object partition: can use bounding volume hierarchy. find bounding box, recursively object partition into child bounding boxes until just a few objects in each set. ray transversal similar to KD-tree

- to split: can do median object split; stop when certain objects/box

now: optimizing splits for BVH

average cost of tracing a ray: cost of leaf node = # of triangles to check. cost of internal node: defined recursively with probabliity

- can be estimated with surface area heuristic

to choose split position: go thru all candidate splits and apply estimation of cost of each