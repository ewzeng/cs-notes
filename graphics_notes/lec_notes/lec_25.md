forward kinematics: given articulated skeleton (including joint types) + parameters for joints (e.g. rotated by XXX), study result

- to animate: give joint parameters as a function of time

inverse kinematics (IK): given skeleton + location of end effector(s), give me the parameters for the joints

- to solve numerically: define error metric, then use gradient descent
- often many solutions (or none at all); can use style-based IK to filter out some solutions (need some training on normal pose data)

weakness of kinematics: time consuming

one soln is rigging: a set of higher level controls that captures all meaningful character changes. different for each character

- can improve on rigging: blend shapes (define a collection of common positions with rigging, and interpolate the transition rigging controls)

now: motion capture (realistic, complex, may require alterations if not meeting artistic needs)

optical motion capture: markers on subject, take videos from multiple cameras, deduce marker position by triangulation, occlusions difficult

facial animation is very hard (uncanny valley - the closer the imitation, the more negative the emotional response, until sufficiently realistic)