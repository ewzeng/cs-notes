Clock algorithm: If no "use", "dirty" PTE bits, use software structure. Trap to OS with "writable" and "valid" bits.

If no "use" bit, can also do second-chance list algorithm (on VAX)

Free list: pageout demon fills free list in background with clock algorithm when below threshold. Dirty pages start copying back to disk when enter list.

Reverse page mapping: hunt down all page tables pointing at given page when freeing the page. Many OS do different things.

How to share memory?

- Each process needs min # of pages in RAM to run
- Page allocation: local (schemes below), global (most OSes)
- Fixed scheme: equal, proportional, priority allocation; adaptive scheme: page fault frequency

To detect thrashing: use working set model

Use clustering (sequential disk reads) to avoid compulsory misses

MELTDOWN BUG. I get it now!! So cool.

- Clear `arr` from cache
- Access stuff at kernel address `x = *address` inside a try catch.
- Out of order branch prediction: allow address while checking if valid.
- Try to access `dummy =  arr[x * 4096]`, now the value of `x` can be found by checking which cache line is loaded. Mutliply by 4096 to prevent cache pre-fetch issues.
- OS realises bad address, flushes everything out. Try catch makes sure no segmentation fault.
- However, the information is still stored in the cache line!!!

#### I/O

Bus: common set of wires for communication plus protocols.

Device interface:

- Block devies: open, read, write, seek; character devices: get, put; network: socket interface
- Blocking, non-blocking, asynchronous interfaces

CPU talks to device controller. Memory mapped I/O: control registers mapped to memory.