Multi-Segment Mode: base + bound for each segment. Advantage: sharing. Problem: fragmentation. Solution: use paging, not base + bound.

Paging:

- Pages can be shared! One example: pintos PT has a "kernel region" (i.e. below PHYS_BASE)
  - Many userland examples too: libraries, many processes running a read-only executable, etc.
- Security: randomize virtual addresses for stack, heap, etc. (buffer overflow attack), separate PT for user processes that doesn't include entire kernel (meltdown attack)
- Multi-level page table: to cut down on the size of page table (PT is sparse)
  - If a page is 4Kb: magic 10-10-12 decomposition (Intel calls PD, PT)
- PTE entry: many control bits (dirty, writable, valid, etc): along with physical page number, make up 32 bits (note no need to store offset)
  - writable allows us to implement copy-on-write

x86 uses both segments and pages; however most modern OS don't use segment registers. Exceptions are FS, GS.

Inverted page table: size of page table $\geq$ VA allowed per process. Use hash tables so PT size independent of # of VAs. Used by some processors.

Next time: we will talk about making memory lookup more efficient (caching!)

- Key measure: average access time