Fully associative may do worse than direct-mapped in certain scenarios

Page fault occurs whenever translation fails - can be page not in PD or paged out, or invalid access

TLB miss for 2-level page table requires two memory accesses (but no extra translation as we will only be working with physical addresses)

MIN/STRF: need to look into the future

Banker's algorithm should be guarateed to avoid deadlock

Clock algorithm: set use bit to 1 on a new page too

Thread block calls the scheduler

If you enforce an globally ordering of which chopsticks to pick first, when you can avoid deadlock