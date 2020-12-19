# Buffer Overflow Attacks

The most common form of attacks are __buffer overflow attacks__. A __buffer__ is a chunk of memory, like an array in C. In a buffer overflow attack, we overwrite memory by providing a larger-than-expected input (and thus overflowing a certain buffer). This type of attack works against systems written in C/C++ because there is no automatic bound-checking for C/C++. Buffer overflows do not work in languages that provide automatic bound-checking, and thus a way to completely eliminate buffer overflow attacks is to write in __memory safe languages__.

One common form of buffer overflow is performed on the stack.

- The goal of this type of buffer overflow is to overwrite the return address `ra` to point to malicious code. This way, when the current function returns, it will start executing malicious code. (This is called __stack smashing__ and was first introduced in the famous paper *Stack Smashing for Fun and Profit* by Aleph One).
- For stack smashing to work, need the malicious code to be somewhere in memory. One method is to overwrite a portion of the stack above `ra` with malicious code after overwriting `ra` (that is, in the buffer, put the malicious code right after the malicious `ra`)

Buffer overflow can also be performed on the heap by overwriting a vtable pointer (a thing in C++). 

If the coder manually does bound checks to defend against buffer overflows, sometimes it is possible to bypass them with __signed/unsigned vulnerbilities__. For instance, suppose we have the following piece of code:
```
char[10] arr;
int n = /* Get user input */
if (n < 10) {
	/* Read n bytes of user input to arr */
}
```
On the surface, it seems that the bound check `n < 10` prevents any possibility of overflowing `arr`. However, the attacker input `n = -1`. This passes the bound check, but `-1` is a large number when interpreted as an unsigned `int`. Under some circumstances, the code may cast `-1` as an unsigned `int` before reading the `n` bytes of user input. Thus, this attacks fools the bound check. __Integer overflow vulnerbilities__ work in a similar fashion (`len + 1` may be small, but `len` can be big).

Another possible memory attack is the __format string vulnerability__. This is not really a buffer overflow attack, but it is somewhat similar, and it occurs when coders use `printf` incorrectly. For instance, suppose we have:
```
printf("/* Get input string from user */");
```
This code is vulerable because of a particular feature of `printf`. That is,
```
printf("%s");
```
will print the string found at the address `*(esp - 4)`. Thus, if the attacker can manipulate the word right below `esp` and then input `%s` to the program, they will be able to read anywhere in memory. (And using `%n`, can also write anywhere in memory). The way to prevent format string vulnerabilities is to use `printf` like so:
```
printf("%s", "/* Get input string from user */");
```

As one may guess, exploits can often be very brittle (and specific to certain machines). Making exploits robust is an art. For instance, in stack smashing, it may be difficult to find the address of the malicious code. To make this robust, the attacker can start the malicious code with 100 NOPs (so if the address lands anywhere in the "NOP-sled", the attack will still work).