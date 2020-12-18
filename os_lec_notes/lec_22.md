#### Distributed Decision Making

Distributed consensus making - many nodes; want all decide on T or F; cannot forget decision

How to solve: two-phase commit, one coordinator; T if everyone T and no time outs

- Always write in log before sending decision to others (to take care of crashing)
- Both workers and coordinators can be implemented as state machines
- Note: coordinator needs to send out a vote request
- 2PC not subject to general's paradox because they do not decide on a time
- Weakness: one node fails $\rightarrow$ the whole system has to block

What if malicious nodes? Byzantine general's problem. Need $n > 3 \cdot \text{malicious nodes}$ to solve.

Blockchain is a distributed decision making algorithm. Can solve Byzantine general's problem.

#### Network Protocols

Vocabulary: various link layers

Broadcast network: a (local) shared medium; old days: a bundle of wires

- messages = header (a MAC address) + body; everyone recieves; those with different address discard
- to avoid message collisions: carrier sense, collision detection, backoff scheme (adaptive randomness)

A switch turns a broadcast network into a point-to-point network. Routers connect different subnets (like switch/broadcast networks).

#### IP

Subnet: hosts have related IPs (differ only in last few digits)

IP packets formats are well-defined; IP can only send messages from machine to machine - not per application

Routing tables (tables of subnets to how to get there) - dynamic algorithm to maintain; no centralized state

Also need a system for names to IP addresses (like www.berkeley.edu): domain naming system - hierarchial

- If DNS not secure - then can route people to fake websites

#### Network Abstraction

Packets: physicial reality; messages: abstraction

- To do process-to-process communication, use ports
- Idea: wrapping headers, then unwrapping headers (going through the different layers)