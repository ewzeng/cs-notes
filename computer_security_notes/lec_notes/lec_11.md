today: intro to networks

protocol: agreement on how to communicate (e.g. syntax)

internet: move data from one place to another

building up the internet:

- build block 1: something that carries data (e.g. wires, radio waves)
- use bb1 to link up people locally (LAN), this is bb2. often shared (need protocol to store destination so other computers know to ignore)
  - machines in a LAN have unique MAC addr (no good for global addressing, only local)
- connect multiple LANs to a central place (router) using bb1. this creates a wide area network (bb3)
- internet: connect a whole bunch of routers. travel by router hop (each router figures out which router to give next to get closer to destination)
  - global addr: IP addr

internet design is partitioned into layers. from lowest to highest: physical layer (wires, radio), LAN protocol (computer to computer or computer $\leftrightarrow$ router), internet protocol (router to router), transport (e.g. TCP, provide extra services), application data

the protocols are "basically" headers; most basic unit of data in the internet for router-to-router: the packet (IP defines the header)

key: moving to lower layers: wrap additional headers; moving to higher layers: peel off headers. sender OS does app $\rightarrow$ packets (apply TCP, IP), and then adds LAN protocol. routers remove LAN protocol and send around packets. last router takes packet, adds LAN protocol, and sends to correct computer. reciever OS then decodes everything, gives data to application.

design decision: routers are dumb (as simple as possible). just try their best. packets may be unreliable and dropped. so need TCP to make more reliable.

TCP has header has sequence numbers, ACK field - this allows resending of data by OS for reliability and a bytestream abtraction. on one machine, different applications have different ports. TCP header also contains this info.

TCP handshake: SYN, SYN-ACK, ACK (set up sequence numbers)

UDP: alt to TCP. only ports, no reliability. but fast. (used by skype)

use DNS server to find IP addr; IP addr assigned and DNS server IP given by a local network server when you connect to a LAN

