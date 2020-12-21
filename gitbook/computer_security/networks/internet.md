# The Internet

In this section, we will give a brief overview of the structure of the internet. A more detailed overview can be found in official course notes found [here](https://cs161.org/assets/notes/networking-notes.pdf). 

## Building the Internet

The purpose of the internet is to move data from one place to another.

* Building block 1 \(bb1\): something that carries data \(e.g. wires, radio waves\)
* Use bb1 to link up computers locally \(e.g. all the computers in a room\). The result is a **Local Area Network \(LAN\)**. In a LAN, communication is usually shared by everyone \(that is, any data sent by any computer is received by all the computers\). Therefore, when communicating in a LAN, every message should have a destination address so computers know to ignore messages not meant for them.
  * Machines in a LAN usually have unique **MAC addresses**, which provides a way to do this. \(This is not to be confused with MACs in cryptography.\)
* Use bb1 to connect to connect each LAN to a **router**.
* Use bb1 to link up routers. The result is the **internet**. To send data from one router to another, the data will travel between linked routers until it arrives at the destination router \(called router-hopping\). More specifically, given a destination address for some data, each router finds a connected router that is closer to the destination, and sends the data to that router.
  * Use **IP addresses** for global addressing

On the internet, data is sent in limited-size chunks called **packets**.

## Protocols

Protocols are needed to communicate on the internet. The two most basic are the following:

* **The LAN protocol** \(i.e. the link layer\): used for communication between two computers on the same LAN or between a computer in the LAN and the router connected to that LAN.
* **The internet protocol \(IP\)** \(i.e. the internet layer\): used for communication between routers.

These protocols are implemented with packet headers. In the LAN protocol, the header of a packet contains the MAC of the destination router or computer. In the internet protocol, the header of a packet contains the IP address of the source and destination computers.

## The Internet in Action

Let's take an example to see the internet in action. Suppose computer **A** wants to send data to computer **B** across the internet. Here is what would happen:

1. **A** breaks up the data into packets, and to each packet, attaches a IP header with the destination address of **B**.
2. To each packet, **A** adds a LAN protocol header with the MAC address of the router. These packets are then sent to the LAN.
3. Because of the router MAC address, the packets are ignored by everyone except the router. The router will strip off the LAN header of each packet, read the destination IP, and then send the packet to another router closer to the destination IP.
4. The packets will router-hop across the internet.
5. Once the router of **B** receives the packets, the router realizes the packets are meant for **B**. The router then adds to each packet a LAN header with the MAC address of **B** as the destination and then sends these packets into \(**B**'s\) LAN.
6. The packets arrive at **B**, who strips the LAN and IP headers from the packets and reassembles them back into one contiguous chunk.

Observe that moving between protocols involves wrapping and peeling headers. More specifically, moving from a lower layer \(link\) to high layer \(internet\) requires peeling headers, and moving from a higher layer to a lower layer requires wrapping headers.

## The Transport Layer

Most of the time, the link and internet layers are not enough for our needs. There is a layer on top of the internet layer called the **transport layer** that provides useful services. There are two possible protocols that can be used in the transport layer:

* **TCP**: the TCP header contains the source and destination port as well as **sequence numbers** and an ACK field to ensure reliable in-order delivery of packets
* **UDP**: the UDP header contains only the source and destination port

To use TCP headers \(or UDP\) when sending data, we proceed very much the same way as the example in the previous section. The only differences are:

* Before attaching an IP header to each packet in step 1, we first attach a TCP \(or UDP\) header.
* After striping the IP header in step 6, we also strip the TCP \(or UDP\) header.

The entries of the TCP header are used in the following manner:

* Source and destination port: allow sending data between different ports on different computers
* ACK field: tells the computers which packets have been dropped and should be resent
* Sequence number: tells the computers the correct ordering of packets when reassembling them

Usually, TCP is preferred over UDP. However, because the header for TCP is larger, UDP is preferred when bandwidth is more important than reliability.

## The TCP Handshake

To communicate with TCP as described in the previous section, computers need to set up initial sequence numbers. This is done with a **TCP handshake**, which occurs at the beginning of a connection:

* Computer **A** sends a SYN packet.
* Computer **B** sends a SYN-ACK packet.
* **A** responds with a ACK packet.

After the handshake, things proceed normally as before: data gets chunked into packets, headers added, sent through the internet, headers stripped, and reassembled.

## Miscellaneous

When your laptop first connects to the LAN, the DHCP \(a local network server\) assigns your laptop a IP addresses and a **DNS server** address.

When you go to a website, your laptop first asks the DNS server for the IP address of the appropriate website server. Then using that IP address, you communicate with the website server \(with probably TCP, so you start off with the TCP handshake\).

