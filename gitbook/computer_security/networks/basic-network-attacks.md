# Basic Network Attacks

Two common network attacks are:

* Eavesdropping
* Injecting packets (called **spoofing**)

To attack a network connection, there are two types of attackers.

* **On-path attackers** control a router that the data passes through.
* **Off-path attackers** do not.

By definition, off-path attackers cannot eavesdrop on a connection. Spoofing packets as an off-path attacker is also diffcult because for a spoofed packet to be accepted by the reciever of a TCP connection, it must have the correct sequence number. Because initial sequence numbers are choosen randomly, this is difficult to do.

On the other hand, on-path attackers are extremely powerful because they can eavesdrop on a connection. They can also easily spoof packets because they can eavesdrop to find out the sequence numbers used.

* When on-path attackers spoof packets, it becomes a race which packet (real or spoofed) arrives at the reciever first.

Another common network attack are **DHCP attacks**, where a malicoius DHCP races a real DHCP to give a bad DNS server and gateway router.