today: defend buffer overflows

- memory safe lang

- if can't: check bounds, code hardening (often used to defend legacy code; stuff implemented in OS or compilers)

##### Bound checking

to verify we got bound checking right

- know preconditions and postconditions of each function
- make caller guarantee preconditions; make callee guarantee postconditions
- to sysmatically derive preconditions: id each point of mem access, write down precondition it requires, propagate requirement up to beginning of function

##### Code Hardening

stack canaries: insert secret value after saved ra, and before returning, check secret value. defends against stack smashing. secret value (canary) changes each time program is run. however, this is weak.

- attackers can try to find out canary (say format string vul), overflow in heap, overwrite other stuff in stack, etc.
- can brute-force guess canary (32-bit value, one byte is null to stop bad call to strcpy)

non-executable pages: mark writeable pages as non-executable (implemented in PT)!

- however, not everything important has to be executable
- return into libc attack: set ra to some libc function, and set the args to that function in stack; then when exiting current frame, code will call that function with attacker's args
- return-oriented programming: chain together "return-to-libc" idea many times
  - find a set of short code fragments (gadgets) from existing code that when called in sequence execute the desired function
  - overwrite the stack so we can the above (many fake stack frames)

address space layout randomization (stack start, heap start, code start randomized etc.) harder for 32-bit architecture

non-exec pages + addr rand makes many exploits harder (state-of-the-art def)

- attacks usually involve finding a vulnerability that leaks information about addrs and then doing a rop attack

##### Fuzz testing

huge random testing

coverage-guided mutation testing: start from valid input, flip bits, measure coverage, keep any inputs that covered new code