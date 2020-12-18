How to choose (sender) window size in TCB? $<$ reciever window size. Both measured in bytes.

- Want: ACK arrive just as we are about to send next packet. Math: Round-trip latency $\times$ bandwidth of slowest link

Parition tolerance: work even if two nodes (which are up) can't communicate

NFS: can get partially updated file.

Andrew File System: tell all people with a copy of the file that files have been updated. Write though on close (so no partial updates). Use disk as cache instead of buffer cache.

New model: instead of thinking of files, think of key value stores (e.g. python dictionaries)

- For instance, FB: userID vs user profile
- Partition the Key-Value table across many machines
- How to locate key-value? Hashing to map key space $\implies$ location.
  - Recursive (directory is botleneck) vs iterative query (scalable, harder to enforce consistency).
  - Replication $\implies$ fault tolerance. 
  - Consistency is difficult. Many different models (like eventual consistency, atomic consistency). One example:
    - quorum consensus - add timestamps to updates for consistency, for speed: wait for $W$ ACKs and $R$ ACKs with $W + R > N$, $N$ is the replica size
  - Need consistent hashing for load balancing (a more dynamic version of hashing). Pictorally, keys on a ring. Map some keys and nodes. To find node for key, find key, then move counterclockwise to find a mapped key. That key maps to the correct node.
    - Chord: distributed lookup service (MIT and Berkeley)
      - Every node knows precessor and successor. Use `stabilize()` for joing operation. Retry if queue crossing operation currently doing `stabilize`
      - To make fast - use a finger table
      - Fault tolerance: replicate a key consecutively on nodes of the chord
      - Kubi: internalize chord!!!