#### G&T § 1.1.1

traditional rubric of security: CIA - confidentiality, integrity, availability

confidentiality: protection of data. common themes:

- encryption of data
- access control based on authentication (usually via pswd, fingerprint, fob, etc.)

integrity: no unauthorized data changes. common themes:

- access control (as above)
- redundancy: checksums, error correcting codes, backups

availability: want data to be available at all times. common themes:

- lots of backups in case one fails



#### Craft § 1-1.1, 1.3

due to modern technology complexity, CIA doesn't cover everything, e.g. where does pirating music fall?

a better way to view security is to think about states (similar to Banker's Alg):

- there are many states, we want to stay in the "good" or "correct" states
- security is the question of keeping the adversary from coaxing us into the "bad" states

the problems we face are:

- our definition of "correct" may be flawed, e.g. gov't defined "correct" tax form processing failed to consider multiple versions of the same tax form being submitted, leading to multiple payouts
- way too many states; too complex

b/c there are almost surely security vulnerabilities, must think about risk management



#### G&T § 1.1.2-4

in addition to CIA, we have AAA: assurance, authenticity, anonymity

- assurance: trust that systems will behave as expected (for users, trust often comes from the reputation of the system)

- authenticity: ability to determine if stuff are genuine (often use digital signatures)

- anonymity: obvious

most common types of attack: eavesdropping, alteration, denial-of-service, masquerading (pretending to be someone else), repudiation (denial of data reciept), traceback (determine source of particular data)

there are ten key security principles:

- simplicity of design
- fail-safe defaults (e.g. if adding a new user, the default user access rights should be minimal)
- complete mediation (check things every time, not just the first time)
- open design! YEET open source (b/c else if leaked, may be irrepairable)
- separation of privilege (split a big privilege into multiple smaller privileges)
- least privilege
- least common mechanism (minimalize sharing)
- want to be usable so users like it
- work factor (take into account who the probable attackers are and make it hard to them to attack)
- compromise recording (sometimes recording is a deterrent - like security cameras)