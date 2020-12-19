# Buffer Overflow Defenses

The easiest way to defend against buffer overflows is to code in a memory-safe language. However, this isn't always possible \(for instance, most OSes and compilers are written in C\). In this section, we discuss some common strategies to defend against buffer overflows when one must use C/C++.

## Bound Checking

The most obvious defense is to always check bounds whenever one is handling user input. In theory, this should defend against all buffer overflow attacks, but in practice, bound checking is annoying to implement and easy to forget or get sloppy with \(see signed/unsigned and integer overflow vulnerabilities discussed in the previous section\). Thus, even with bound checking, one should implement other defenses.

## Stack Canaries

The idea of stack canaries is to insert a secret value \(called the **stack canary**\) after each saved `ra` on the stack. Before the program returns to that `ra`, a check is done to make sure the stack canary is unchanged. This way, programs can ensure that the saved `ra` has not been overwritten.

* To prevent attackers from guessing the stack canary, the stack canary should be randomly chosen each time a program is run.

Stack canaries make it more difficult for stack smashing but is a weak defense by itself.

* Attackers can try to find out the canary \(using, say, a format string vulnerability\)
* Attackers can still buffer overflow in the heap, or overwrite non-`ra` entries on the stack
* If the canary is 4 bytes, the attacker can try to guess the canary with brute force. \(It helps that the last byte of the canary is always a null terminator to defend against `strcpy` attacks\)

Stack canaries are implemented by the compiler. The next two defenses are implemented **in the OS**.

## Non-Executable Pages \(W^X\)

The idea of non-executable pages is to mark all writeable pages as non-executable. This way, the attacker cannot introduce malicious code into the system and execute that code \(via stack smashing, for example\).

However, there are clever ways to get around this.

* In the **return-into-libc** attack, the attacker can set the saved `ra` to some libc function and then manipulate arguments on the stack. Then, when exiting the current frame, the code will call that libc function with arguments provided by the attacker.
* One can generalize the return-into-libc attack to something called **return-oriented programming \(ROP\)**. The idea is to find a set of code fragments \(called gadgets\) from libc that when called in sequence execute the desired malicious function. Then the attacker can then stack smash and create many fake stack frames in such a way that the gadgets are executed sequentially.
  * **ROP-Compilers** help attackers find gadgets to execute whatever function they want.

## ASLR

ASLR stands for **address space layout randomization**. The idea of ASLR is to randomize the starting points of the stack, heap, and code. This way, even if the attacker is able to introduce malicious code into memory \(or find gadgets to create malicious code\), the attacker will not know where the malicious code is. In particular, this prevents ROP and return-into-libc attacks.

In fact, the current state-of-art defense \(implemented by all major OSes\) is ASLR with W^X. Attacking such systems often requires first finding a vulnerability that leaks information about addresses, and then doing a ROP attack. \(For more information, see the paper _ASLR Smack & Laugh Reference_ by Tilo Muller.\)

