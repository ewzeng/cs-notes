want designed smooth curves, surfaces

spline: piecewise smooth curve that we can control

cubic hermite interpolation. input: values + deriv at endpoints; get cubic poly. use to build hermite spline (we control certain points and derivatives).

catmull-rom interpolation. input: points. rule for derivatives: match slope between previous and next values. then apply cubic hermite.

- can generalize to points in N-dim

interpolation schemes determined by set of basis functions: given input $p_i$ (which are points/derivatives/vectors), interpolation is $\sum p_i F_i(t)$

- $H_i(t)$ for hermite, $C_i(t)$ for catmull-rom, bernstein polynomials $B_i(t)$ for bezier

cubic bezier interpolation: 4 control input points in 2D+. go thru $p0, p3$. deriv at $p0$ is  $3(p1-p0)$ and similar for $p3$.

de Casteljau alg: "corner cutting" recursive subdivision to draw beizer curves. also gives algebraic formula for beizer curves (using a pyramid of coefficents). this is actually the best starting def of bezier curves.

what about many point inputs? can do splines (i.e. piecewise), or higher order interpolation (but latter hard to control). a-frame construct gives $C^2$ continuity

bezier curve properties: affine transformation property, convex hull property

cubic bezier surfaces. input: 4x4 control points. define by moving bezier curves. evalution: two iterations of de Casteljau. doesn't matter which direction we first go. algebraic formula is a tensor product!! similar critertions for continuity on splines.