Byzantine general:

- One app: incoming request = general; if have enough nonmalicious servers, can correctly service the request.

Queuing theory:

- If arrival distribution not known, assume memoryless (i.e. normal).
- Variables:
  - $\lambda =$ arrival rate; $\mu = \frac{1}{T_{ser}} = $ service rate; $T_{sys} = T_{queue} + T_{ser}$
- Little's theorem: (arrivial rate) $\times$ (time in queue) $=$ length of queue

End-to-end principle: don't work too hard in the middle.

Tricky definitions:

- Indirect blocks: non-inode block that points to data; doubly indirect: non-inode block that points to indirect blocks, etc.

Reminders:

- Don't forget to update size and write the updated inode back to disk when extending files!

Disk equations:

- $T_{ser} = T_{ctrl} + T_{seek} + T_{rot} + T_{xfer}$

- $\text{Disk Bandwidth} = \frac{\text{bytes xfered}}{T_{ser}}$
- \# of disks proportional to IOPS (blocks read per second)

TCP window size for max bandwidth: If reciever window size unlimited, sender w.indow size should be the amount of bytes that can be sent just before the first ACK arrives (need to know transmission bandwidth). If reciever window size given, take the min of the two values.

Erasure coding: store polynomial coefficents, a generalization of RAIDX (RAIDX is just XOR)Z

Priority inversion is not a deadlock - it is a livelock. Starvation (indefinite waiting) and deadlock (circular wait) are also different things.

Most processors can't modify the TLB directly, so the TLB is not modified on a page fault. (Hardware complexity)

The worst case scenario of LRU replacement is sequential flooding.