#### Address Translation

AMAT = (Hit rate $\times$ Hit time) $+$ (Miss rate $\times$ Miss time)

- Miss time = Hit time $+$ Miss penalty

MMU: the hardware that does memory translation (i.e. page table lookup)

TLB: "page table cache"

- Small (128-512 entries), fully associative, sometimes a TLB slice in front
- TLB + cache access can be overlapped (use TLB offset to look for the index in the cache while TLB looks for the page to go with offset)! Works if index $\subset$ offset.
- Often different TLBs for instructions and data

Page faults (failed translation) are traps (synchronous)

- Page faults are precise exceptions (all instructions up to exception completed, offending instruction acts as if not started)
- Reasons: privilege violation, PTE invalid
- PFs tries to get OS to fix situation and retry instruction (fundamental inversion of hardware/software boundary!!); cannot be resolved $\implies$ terminate process
- If what we want in disk: PF handler pulls stuff off disk, updates PT
  - Demand paging: DRAM as a cache of disk

#### Appendix on Caches

Sources of cache miss:

- Compulsory miss: miss due to first reference
- Capacity miss: miss due to cache too small
- Conflict miss: miss due to small associativity (run against fully associative cache)
- Coherence miss: due to multiprocessor

Types of caches: direct map, N-set associative, fully associative

- The index of a block is implicit in a cache, not stored!

Replacement policy:

- LRU vs. random doesn't matter very much for a large cache; LRU good for small caches (like TLB)

Cache writes

- write-through: write also to DRAM
- write-back: only write to cache (more complex, faster)