today: "FYI" lecture, advanced materials

often, rendering is too perfect

can define some fine details with normal maps

raytracing detailed microfacets impossible (20 days to converge!); instead, if pixel projects onto patch $p$, compute distribution of normals in patch $p$ (with normal map), and plug into microfacet BRDF equation

recent trend: incorporate wave optics

hair: can be seen as many cylinders. surface of cylinder = tilted staircase. medullar of hair scatters light, so medullar can be modeled as a cylinder within a hair strand cylinder. fur has large medullar, human hair less.

- raytracing slow (need at least 100 bounces per ray). observation: fur looks like clouds (many bounces blur things out). soln: use neural network to map fur parameters to cloud parameters, then render as clouds (have methods to do so)

participating media: cloud & fog & translucent material. phase function define scattering behavior (the analog of BRDF). do a random walk of light ray (taking into account the phase function)

- for translucent material, this random walk can be seen as subsurface scattering and can be modeled with a BSSRDF

cloth: can be rendered as a surface with microfacet model. but also can be rendered as participating media. or render as hair fibers.

granular material: compute on-the-fly (to save storage). called procedural appearance. similarly, can define texture details by computing noise functions on the fly.