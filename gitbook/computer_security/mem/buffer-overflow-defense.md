# Buffer Overflow Defenses

The easiest way to defend against buffer overflows is to code in memory safe languages. However, this isn't always possible (for instance, most OSes and compilers are written in C). In this section, we discuss some common strategies to defend against buffer overflows when one must use C/C++.

## Bound Checking

The most obvious defense is to always check bounds whenever one is handling user input. In theory, this should defend against all buffer overflow attacks, but in practice, bound checking is annoying to implement and easy to forget or get sloppy with (see signed/unsigned and integer overflow vulnerabilities discussed in the previous section).

Thus, even with bound checking, one should implement other defenses. We discuss three defenses implemented __in the OS__ running the target program: stack canaries, non-executable pages, and ASLR.

## Stack Canaries

In the stack canary defense, the OS inserts a secret value (called the __stack canary__) after each saved `ra` on the stack. Before the program returns to that `ra`, check to make sure the stack canary is unchanged. This way, the OS can ensure that the saved `ra` has not been overwritten.

- To prevent attackers from guessing the stack canary, the stack canary should be randomly chosen each time a program is run.

Stack canaries make it more difficult for stack smashing, but is a weak defense by itself.

- Attackers can try to find out the canary (using, say, a format string vulnerability)
- Attackers can buffer overflow in the heap, or overwrite other stuff in stack
- If the canary is 4 bytes, the attacker can try to brute-force guess the canary (the last byte of the canary is always a null terminator to defend against `strcpy` attacks)

## Non-Executable Pages (W^X)

Another defense against buffer overflows is to mark all writeable pages as non-executable. (This implemented in the page table). This way, the attacker cannot introduce malicious code into the system and execute that code (via stack smashing, for example).

However, there are clever ways to get around this.

- In the __return-into-libc__ attack, the attacker can set `ra` to some libc function, set the args to that function in the stack. Thus when exiting the current frame, the code will call the libc function with arguments provided by the attacker.
- One can generalize the return-into-libc attack to something called __return-oriented programming (ROP)__. The idea is to find a set of short code fragments (gadgets) from libc that when called in sequence execute the desired malicious function. Then the attacker can then stack smash and create many fake stack frames in such a way that the gadgets are executed sequentially.

## ASLR

ASLR stands for address space layout randomization. The idea is that randomize the starting points of the stack, heap, and code. This way, even if the attacker is able to introduce malicious code into memory, the attacker might not know where the malicious code is. This prevents ROP and return-into-libc attacks.

In fact, the current state-of-art defense (implemented by all major operating systems) is ASLR with W^X. Attacking such systems often require first finding a vulnerability that leaks information about addresses, and then doing a ROP attack. (For more information of bypassing ASLR, see the paper *ASLR Smack & Laugh Reference* by Tilo Muller.)