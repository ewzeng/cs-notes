today: physical simulation

#### mass + spring systems

bunch of masses connected by bunch of springs; can simulate rope, hair, clothe

use non-zero length springs + motion damping (behaves like viscous drag, avoid oscilllating forever)

- careful: want to only damp force from springs

problem: if split spring into two smaller springs, the two smaller springs need larger spring constant for system to behave same as before. soln: to avoid having to redefine spring constants after splitting (i.e. discretizing more), define spring constants in terms of ($\Delta$ in length) / (original length), not just  ($\Delta$ in length)

mass + spring systems are examples of particle systems

#### simulating particle systems

euler's method: calc current accl. from force, use current accl. to update velocity, and current velocity to update position

- simple and common, but inaccurate and instable as errors accumulate (we are basically performing numerical integration)

fundamental problem of simulation: instability (blow up)

to combat instability: modified euler (avg start and end velocity), adaptive step size (reduce step size until reducing more doesn't help accuracy), implicit euler (great but very complicated, solve for future derivatives), verlet integration (project 4!)

- verlet integration: after modified euler, constrain positions of particles (will dissipate energy $\rightarrow$ stabilize). fast, simple, but not physically based