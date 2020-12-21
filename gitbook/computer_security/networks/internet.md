# The Internet

In this section, we will give a brief overview of the structure of the internet.

## Building the Internet

The purpose of the internet is to move data from one place to another.

- Building block 1 (bb1): something that carries data (e.g. wires, radio waves)
- Use bb1 to link up computers locally (e.g. all the computers in a room). The result is a __Local Area Network (LAN)__. In a LAN, communication is usually shared by all everyone (that is, any data sent by any computer is recieved by all the computers). Therefore, communication in a LAN requires a protocol to store the destination computer so computers know to ignore messages not meant for them.
  - Machines in a LAN have unique MAC addresses, which provides a way to do this. (This is not to be confused with MACs in cryptography.)
- Use bb1 to connect to connect each LAN to a __router__.
- Use bb1 to connect a whole bunch of routers. The result is the __internet__. To send data from one router to another, the data will often have to travel through intermediate routers (called router-hopping). More specifically, given a destination address for some data, each router finds a connected router that is closer to the destination, and sends the data to that router.
  - Use __IP addresses__ for global addressing

## Protocols

To communicate, protocols are needed. The two most basic are the following:

- **The LAN protocol** (i.e. the link layer): used for communication between two computers on the same LAN or between a computer in the LAN and the router connected to that LAN.
- **The internet protocol (IP)** (i.e. the internet layer): used for communication between routers.

To support these protocols, messages are sent with a header. In the LAN protocol, the header contains the MAC of the destination router or computer. In the internet protocol, messages between routers are split up into limited-size **packets**, the header of the packet containing the IP address of the source and destination computers.

## The Internet in Action

Let's take an example to see the internet in action. Suppose computer __A__ wants to send data to computer __B__ across the internet. Here is what would happen:

1. __A__ breaks up the data into packets. That is, __A__ breaks up the data into small chunks, and to each chunk, attaches a IP header with the destination address of computer __B__.
2. To each packet, __A__ adds a LAN protocol header with the MAC address of the router. __A__ then sends all these "packets" to the LAN.
3. The computers in the LAN ignore these "packets" because the MAC address is not meant for them. The router in the LAN, on the other hand, realizes these "packets" are for it, so it will strip the LAN header off of each "packet", read the destination IP, and then send the packet to another router closer to the destination IP.
4. The packets will router-hop across the internet.
5. Once the router of computer __B__ recieves the packets, the router will realize the packets are meant for computer __B__. The router will then add to each packet a LAN header with the MAC address of computer __B__ as the destination and then sends the "packets" into the LAN.
6. The "packets" arrive at computer __B__, who strips the LAN and IP headers from the packets and assembles them back into one contiguous chunk.

Observe a few things:

- Moving between protocols involves wrapping and peeling headers. More specifically, moving from a lower layer (link) to high layer (internet) requires peeling headers, and moving from a higher layer to a lower layer requires wrapping headers.
- When we say "packet", we mean a packet with a LAN header attached to it.

## The Transport Layer

Most of the time, the link and internet layers are not enough for our needs. There is a layer on top of the internet layer called the __transport layer__ that is often needed. There are two possible protocols that can be used in the transport layer:

- __TCP__: the TCP header contains source and destination port for the ability to send data between different ports on the same computer, as well as __sequence numbers__ and a ACK field to ensure dropped packets are resent and all packets can be reassembled in the correct order
- __UDP__: the UDP header contains only the source and destination port

To use TCP headers (or UDP) when sending data, we proceed very much the same way as the example in the previous section. The only differences are:

- Before attaching an IP header to each chunk in step 1, we first attach a TCP header.
- After striping the IP header in step 6, we also strip the TCP header.

Usually, TCP is preferred over UDP. However, because the header for TCP is larger, UDP is preferred when bandwidth is more important than reliability.

## More About TCP

TCP works in the following manner:

- When two computers want to communicate, they do a TCP handshake. Computer __A__ sends a SYN packet, computer __B__ sends a SYN-ACK packet, and __A__ responds with a ACK packet. This allows __A__ and __B__ to set up initial sequence numbers.
- __A__ and __B__ communicate data.
- The ACK fields in the TCP headers tell the computers which packets were dropped and should be resent.

Throughout this whole process, all packets sent have TCP headers wrapped inside the IP headers (see previous section).

(Unforunately, this was a rather brief description of TCP. To get a better idea of TCP (and networks as a whole), please see the official course notes found [here](https://cs161.org/assets/notes/networking-notes.pdf).)

## How Things Start

We have talked about how two computers send data over the internet, and the various protocols involved. Now we provide a brief description of what happens when you walk into a coffee shop and connect your laptop to the internet:

1. When your laptop first connects to the LAN, the DHCP (a local network server) assigns your laptop a IP addresses and a DNS server address.
2. When you go to a website, your laptop first asks the DNS server for the IP address of the appropriate website server. Then using that IP address, you communicate with the server.

