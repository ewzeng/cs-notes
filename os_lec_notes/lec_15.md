Demand paging: DRAM as disk cache

- Backing store: pages in RAM also in disk (why dirty bit needed in PTE)

- "Illusion of infinite memory" is imprecise; should be "illusion of vast memory."

Different OSes use different ways to keep track of pages on disk

- Hash tables

- PTE entry: if present (valid) bit = 0, all other bits can be used by OS in any way (e.g. to store data to help find on disk).

OS keeps a free list of pages

Page faults bad. $\frac{1}{1000}$ chance = 40 $\times$ slowdown

- Compulsory misses: handled by prefetching
- Capacity miss: page a few processes to disk and focus on a few first
- Conflict miss: none (we are fully associative!)
- Policy miss: due to bad replacement policy

Page replacement policy

- Random: unpredictable
- MIN (replace page that won't be used for the longest time): provable optimal; can try to use past to predict future
- LRU is good, but has higher overhead. In practice, people approximate LRU:
  - Clock algorithm: arrange physical pages in circle with single clock hand. Hardware sets use bit on each reference, clock unsets use bit when going hand, using the first page without use bit to replace. (Can be generalized to N-th chance)
- FIFO bad. Trivia: Belady's anomaly (adding memory hurts)
