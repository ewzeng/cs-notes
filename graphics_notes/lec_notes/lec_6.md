#### Visibility

visibility problem: want front objects on top of back objects

- painter's alg: paint from back to front (but very hard to implement). Z-buffer alg (easy to implement and faster): store min depth in a Z-buffer.

#### Shading

to apply shading, multiply it with the texture color of that pixel

blinn-phong: shading = specular hightlights + diffuse reflection + ambient lighting; we want to compute the light reflected from surface toward the camera

- diffuse reflection: light that is scattered uniformly in all directions (use lambert's cosine law + light falloff to compute amount of light scattered)

- specular highlights: light whose intensity depends on view direction (intensity brightest near "mirror direction" - take dot of half vector and normal; parameter $p$ to control how "mirror-like" the surface is)

- ambient lighting: add constant lighting to everything (approximates light bouncing of walls and other stuff)

shading triangle meshes: flat shading, interpolation of vertices, or interpolation of normals of vertices

- to get normal of each vertex, use underlying geo or average surrounding face normals

shading very computation intensive (more than rasterization)

#### Graphics Pipeline

- input 3D vertices + openGL primitive command (say triangles)
- first step: transformations and perspective projection
- then rasterize each triangle; get a fragment for each triangle
- shade and add texture to each fragment
- combine the fragments into a final frame buffer using the Z-buffer alg