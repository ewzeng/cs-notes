material == BRDF (if take refraction into account as well, called BSDF, but used interchangably). 

can use texture to define a varying BRDF. diffuse BRDF = albedo / $\pi$, albedo = color

refraction: determined by snell's law, index of refraction. no soln means no refraction (e.g. more dense $\rightarrow$ less dense)

fresnel term: reflectance amount also depends on viewing angle (in addition to lambertian $\cos$). grazing angle most. (think: water surface becomes reflective at near horizontal angle)

microfacet material: macroscale (flat & rough) vs microscale (bumpy & specular). bumps = microfacets. microfacet BRDF key: dist of microfacets' normals. how much reflected $wi \rightarrow wo$ depends on the amount of normals in direction $(wo + wi) / 2$.

- also takes into account fresnel + shadowing-masking term

isotropic material: surface normals random (only need relative azimuthal angles); anisotropic material: surface normals same in certain direction (need exact azimuthal angles). defines "directionality" of surface.

BRDFs linear, follow reciprocity law

can measure BRDF of materials from real world instead of doing theoretical modeling