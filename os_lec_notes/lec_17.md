Device controller can interact with CPU in two ways

- CPU uses special instructions to write to control registers
- memory mapped (more common)

DMA: give controller access to mem bus; ask it to do data transfer, interrupts CPU when done

Polling and interrupts often combined

Devide drivers

- `ioctl()` is device-specific
- top half (read, write, etc) vs bottom half (run as interrupt routine)

Performance

- Latency, bandwidth, overhead; for $b$ bytes, latency($b$) = overhead $+$ $\frac{b}{\text{Bandwith}}$
- effective BW $=$ $\frac{\text{transfer size}}{\text{latency}}$

Storage devices

- Disk: unit of transfer = sector; cylinders; seek time $+$ rotational latency $+$ transfer time
  - Key is to minimize seek and rotation delays; lots of intelligence in controller
- NAND Flash: handle random memory well, writing slow (written in pages, erased in blocks)