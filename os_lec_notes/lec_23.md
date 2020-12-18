 Goal of layering: build complex services from simpler ones

- UDP: minimal header to create process-to-process communication, but unreliable
- How to make reliable?
  - A $\rightarrow$ B package; B $\rightarrow$ A ACK. Retransmit if not found. Put sequence number of messages to prevent message duplication.
  - Better idea: (windowing protocol) send packages with seqeunce numbers 1 to $n$ simultaneously, then wait for the ACKs; ACK $m$ says recieved packages up to $m$
    - Here, sequence numbers don't mark duplicate messages but the order. If get two messages with same sequence number, then throw one out.
  - TCP: provides reliable byte stream between two processes
    - Behind the scenes: fragment byte stream into packets, uses windowing protocol; adjusts rate of transmission to avoid congestion
    - Reciever has to tell sender a window size so sender does not send too much
    - How do we agreee on the start sequence number? Must be hard to predict.
      - 3-Way Handshake (contect listen accept)

Now we can send messages. Abstraction: messages and mboxes.

Remote Procedure call: wrap things up as procedures, but actually doing stuff across networks (like TCP/IP, putting messages together, handling big/little endian)

- problem: non-atomic failures
- can be used to construct microkernels

Now, we are ready to discuss storage over networks

- CAP Theorem: can get two of the three: consistency, availability, partition-tolerance
- Distributed filesystems:
  - Need to mount remote filesystem
  - VFS: the abstraction for different types of file systems (virtual blocks, inodes, etc)
  - To be fast - add caches. But then cache consistency problems. To solve:
    - client polls server every 30 seconds
  - NFS (sun) defines a RPC protocol for clients to interact with a file server