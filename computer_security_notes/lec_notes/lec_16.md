today: denial of service (DoS)

DDoS = distributed DoS, cool story: greatcannon on greatfire.org

idea: either find bug to crash program, or perform resource exhaustion (most common)

no silver bullet defense for DoS (esp. since network is fundamentally suited for it)

##### network DoS. basic idea: flood packets

- DDoS: flood packets from many sources. amplification: make innocent users (patsies) flood packets for you

- can overwhelm target's internet connection, or overwhelm the router

one defence: install network filter to discard any packets with certain IP/patterns. need to do the filtering before the bottleneck internet link / bottleneck router. but filters easily evaded (esp. with DDoS).

DoS is a resource fight, so asymmetries are dangerous (i.e. attacker uses little resources but defender needs a lot). e.g. amplification

DNS amplification: DNS reply much longer than request. so small attacker packet spoofed with victim IP yields large flooding packet to the victim

- can to generalized to other UDP based protocols (as need to guess sequence #s for TCP)

SYN-Flooding: for each SYN packet, server allocates some memory for state info (buffers, timers, counters, etc.) so flood with SYN packets = use up server memory

- defense: SYN cookies (avoid keeping memory while doing the 3-way handshake). do this by encoding some state info + HMAC into SeqNum.

##### application-layer DoS (i.e. not network)

to DoS a hive machine: fork a zillion processes, create a lot of files, etc.

one idea: make queries that make application do a lot of work

- algorithmic complexity attack: trigger worst-case runtime of algs / data structures (e.g. hash tables can be slow). defense: use alg with good worst-case run time.
- defenses: only let legit users issue expensive requests, force users to waste some time / resources, provide lots of computing capacity
