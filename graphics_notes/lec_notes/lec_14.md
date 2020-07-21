to draw a random value from given PDF: compute CDF and use inversion method

to uniformly sample unit circle: can do rejection sampling

now: global illumination

in the past, we have we doing direct illumination (stop bouncing at diffuse surfaces)

material reflection: ideal specular (mirror), ideal diffuse, glossy specular, retro-flective

- BRDF = material reflection function (takes input & output direction)
- reflection function = BRDF $\times$ amount of input light, then $\int$ over all incoming dir
  - note incoming radiance depends on reflected radiance at another point in the scene - which is given by transport func

reflection func + transport func + light emitted = rendering equation

reflection, transport func can be seen as linear operators on $L_O$  (function describing light output at every point on scene and angle) and $L_i$ (light input ditto). then rendering eq becomes $L_o = L_e + K(L_o)$, $K = R \circ T$ 

- $K$ is the one-bounce reflection operator