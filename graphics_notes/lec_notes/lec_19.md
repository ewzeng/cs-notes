electronic shutter: pixel reset to starts exposure, reading out pixel ends exposure. readout takes time, so stagger reset to ensure uniform exposure for each pixel (but get rolling artifacts)

- focal plane shutter (quickly move slit across sensor) has same problem

maxwell proved no ideal lens: cannot take all rays coming from one point and project all of them to a point on sensor. we can only approximate

today: ideal thin lens

thin lens: rays from point in object space intersect at a point in image space (conjugate points). conjugate of focal point is point at infinity (i.e. horizontal rays). 

use similar triangles to prove thin lens equation (the relation between conjugate points)

to focus on objects at different distances, move sensor position (or move lens)

lenses: 3D obj $\rightarrow$ 3D obj, sensor extracts 2D slice

out of focus: conjugate point not on sensor slice. defocus blurs are circular ("circle of confusion") because lens aperture is circular (by same reason, circle of confusion at fixed depth is proportional to aperture size)

so far, our ray tracing has been based on a pinhole model. if we raytrace based on thin lens behavior, we can get cool defocus blur
