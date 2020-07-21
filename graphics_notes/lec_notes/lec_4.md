#### 2D-transforms 

basic transform: rotate, translate, scale

naive: 2D-transforms = 2x2 matrices; but to take care of translation, need to add a third coordinate; thus transforms = 3x3 matrices; this is called homogenous coordinates

homogenous coordinates rules:

- point w-coord = 1, vector w-coord = 0; valid op if w-coord result is 1 or 0

two interpretations of transforms: transforming objects, transforming reference frames

#### 3D-transforms

also use homogenous coordinates (4x4 matrices), same rules

any rotation can be decomposed into $R_x, R_y, R_z$, amount of each = Euler angles

- another decomposition: move to z-axis, rotate, move back
- rodrigues' rotation formula

#### Hierarchical Transforms

tree representation of a group of objects

- tranform of leaf-node shape is composition of all transforms on path from root node to leaf (good for modeling a complex group of objects like the human body)
- implemented with pushmatrix, popmatrix

#### Viewing and Perspective

standard camera space: at origin, looking down -z axis, up is +y axis, right is +x axis

orthographic projection: ignore z axis to get 3D camera space $\rightarrow$ 2D image; but no perspective! thus use pinhole camera model

pinhole camera model: do a perspective projective tranform (this is not linear, but can use homogeneous coordinates to turn into a matrix, but need a slight generalization!!)

- first determine view plane; then set some perspectives (angle of view, aspect ratio and viewing volume); then do the transform
  - note: near clipping plane often used as view plane
- the generalization of homogeneous coords: define the points $(wx, wy, wz, w)^T = (x, y, z, 1)^T$