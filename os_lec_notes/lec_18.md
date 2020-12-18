###### Recall

Disk Latency $=$ Queueing time $+$ Controller time $+$ Seek time $+$ Rotation Time $+$ Xfer Time

After a while, flash memory wears out (electrons leak to certain places)

Key for file systems: seek as little as possible

###### Queuing Theory

Some more metrics:

- Service rate $\mu = $ operations per second
- Arrival rate $\lambda = $ requests per second
- Utilization $u := \frac{\mu}{\lambda}$

To model bursty arrival times: use Guassian (aka memoryless) starting at the peak. Bursts and high utilization leads to queuing delays

Squared coefficient of variance $C = \sigma^2 /m^2$

Queuing Theory applies to long term steady state behavior, i.e. arrival rate $=$ departure rate. Arrivals and depatures characterized by some probabilistic distribution.

Little's law for stable systems: avg # of jobs in system $=$ arrivial rate $\times$ response time

Given $\lambda$, $T_{ser}$, $C$ (for arrivals),  then we get $\mu$, $u$, $T_{que}$, $L_{que}$ 

- $T_q = T_{ser} \times \frac{1}{2}(1+C) \times u/(1-u)$

###### Other

Disk optimization: FIFO fair, but long seeks. SSTF (shortest seek time first). SCAN (an elevator algorithm), circular scan (only in one direction).

Directory: index mapping names to files (a file itself)

Logical block addressing (close address = close on Disk)

File system needs to transforms blocks into Files and Directories. Need to track free disk blocks, track which blocks contain data for which files.