today: texture mapping (putting images on objects)

map texture space (the image) onto a surface. each surface point assigned a texture coordinate (u,v)

this class: maps will always be given; finding good maps requires diff geo, etc.

one way to define a texture mapping is to define a map between a bunch of triangles, and then use barycentric coordinates to interpolate the rest

to draw texture, sample texture map over surface. problem: resulting sampling frequency on texture space varies!

goal: want one/few texels per pixel. there are two problems: texture magnification (many pixels per texel), minification (many texels per pixel, where aliasing happens)

texture magnification: apply texture map to pixel. color pixel to nearest texel center (box filter), or do some interpolation (given pos w/r/t neighborhood texel centers)

texture minification: low-pass and then downsample texture file. then do sampling.

because texture sampling varies, we want to use methods fighting texture magnification is some parts of the image, and methods fighting texture minification in other parts. this is a future lecture.