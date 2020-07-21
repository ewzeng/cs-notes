today: buffer overflows; idea: overwrite memory by providing a larger than expected input

works in C/C++ because no auto bound-checking (memory-unsafe); thus many languages always bound-check and hence avoid buffer overflows

buffer overflow on stack: 

- can overwrite the return address (stack-smashing) 
- need the malicious code in memory for this to work; one method is to also put the malicious code in the buffer (directly after the new ra)

sign/unsigned vulnerability: -1 is small, but it is a large number when interpreted as unsigned. this is one way attackers fool bound checks.

- integer overflow vulnerability works in similar fashion (len+1 may be small, but len can be big)

other memory attacks:

- format string vulnerability: if attackers can control the format string, can write to memory using %n (or read memory with %d, %x, %s)

buffer overflow on heap: overwrite the vtable pointer (a thing in C++)

exploits can often be very brittle (specific to certain machines); making exploits robust is an art:

- start malicious code with 100 NOPs (so your address can be a little off)

how to be memory safe: secure coding practices, safe languages, testing