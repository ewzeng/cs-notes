firewall: a chokepoint (i.e. reference monitor) for traffic between internal network and internet (basically a filtering gateway router)

firewall enforces an access control policy for inbound connections (not outbound)

- for traffic not mentioned in policy: default deny is recommended (but default allow is more flexible)

stateless packet filter: most simple firewall, inspects packets with certain rules to determine pass/block. remembers no history. stateful packet filter: keeps track of all connections, each rule specifies which connections are allowed/denied.

filtering connection for a bad keyword not so easy! can split keyword across multiple packets, packets may arrive in different order

- TTL attack: repeat packet seq#'s with different contents but set TTL so that the repeat packets will be dropped after firewall but before recieving server. causes confusion because firewall needs to reconstruct message, but doesn't know which packets to use, and keyword gets to the reciever

application-level firewall: firewall acts as proxy (client $\rightarrow$ server TCP connection becomes 2 TCP connections: client $\rightarrow$ firewall, firewall $\rightarrow$ server). defends against TTL attack

VPN = a way for outside users to authenticate themselves and tunnel past the firewall, as if they were internal users (done by connecting to a internal VPN server + authenticating themselves there)

common firewall bypass: compromise internal machine, then attack from inside