solving rendering eq, get

- $L_o = (I-K)^{-1}L_e \implies L_o = L_e + K(L_e) + K^2(L_e) + \dots$
  - intuitively: add one bounce, then two, then three, etc.
- note we need $\|K\|<1$ to do the series. however we satisfy this because it means stuff doesn't get brighter at each light bounce

putting things together: do a ray cast. compute one bounce to light sources, two bounces to light sounces, etc.

how do we sum over all light paths? recursion + monte carlo sampling of direction (trace to next surface point and choose a random reflection direction at that surface point by importance sampling BRDF) + probabilistic termination (can choose $p_{rr}$ depending on scene)

- the key of all this probability/monte carlo stuff: always divide by the probability - this keeps expected value what we want
- "russian roulette monte carlo"

but this is noisy. so add another tweak: one bounce (direct) lighting (non-recursive, importance sample lights), indirect lighting (recursive, importance sample BRDF)

- this emphasizes the direct lighting part (which generally is more important)

for ray casting, often do multiple rays per pixel

implementation: floating point rounding can have large effects