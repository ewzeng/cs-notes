Buffer cache has delayed writes. So need recovery mechanisms!

Important benchmarks: availability, durability, reliability (all measured in "nines" of probability)

How to make file systems durable? Reed-Solomon error correcting codes to test for failure. Battery-backed RAM for dirty blocks in buffer cache. Make sure data survives long term (RAID 1, 5+).

How to make reliable? 

- Can sequence order of disk operations carefully. Then have a recovery process after failure.
- Can never update anything in place. (copy on write) ZFS works this way.
- Transactions (either everything commits or nothing commits). We jump from consistent state to consistent state. Use a log. (journaling)

