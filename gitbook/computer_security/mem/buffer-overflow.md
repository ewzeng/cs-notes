# Buffer Overflow Attacks

The most common form of attack is **buffer overflow**. A **buffer** is a chunk of memory, like an array in C. In a buffer overflow attack, we overwrite memory by providing a larger-than-expected input \(and thus overflowing a certain buffer\). This type of attack works against systems written in C/C++ because there is no automatic bound-checking. Buffer overflows do not work in languages that provide automatic bound-checking, and thus a way to completely eliminate buffer overflow attacks is to write in a **memory-safe language**.

One common form of buffer overflow is performed on the stack.

* The goal of this type of buffer overflow is to overwrite the saved return address `ra` to point to malicious code. This way, when the current function returns, it will start executing malicious code. \(This is called **stack smashing** and was first introduced in the famous paper _Stack Smashing for Fun and Profit_ by Aleph One\).
* For stack smashing to work, one needs the malicious code to be somewhere in memory. One method to introduce malicious code is to include it in the stack smashing attack. That is, after overwriting the saved `ra`, one can overwrite the memory above the saved`ra` with malicious code.

Buffer overflow can also be performed on the heap by overwriting a vtable pointer \(a thing in C++\).

If the coder manually does bound checks to defend against buffer overflows, sometimes it is possible to bypass them with **signed/unsigned vulnerabilities**. For instance, suppose we have the following piece of code:

```c
char[10] arr;
int n = /* Get user input */
if (n < 10) {
    /* Read n bytes of user input to arr */
}
```

On the surface, it seems that the bound check `n < 10` prevents any possibility of overflowing `arr`. However, the attacker can input `n = -1`. This passes the bound check, but under some circumstances, the code may cast `n` to an unsigned `int` before reading the `n` bytes of user input. As this turns `n = -1` into a large number, this attacks fools the bound check. **Integer overflow vulnerabilities** work in a similar fashion \(i.e. `len + 1` may be small, but `len` can be big\).

Another possible memory attack is the **format string vulnerability**. This is not really a buffer overflow attack, but it is somewhat similar, and it occurs when coders use `printf` incorrectly. For instance, suppose we have the code:

```c
printf("/* Get input string from user */");
```

This code is vulnerable because of a particular feature of `printf`. That is,

```c
printf("%s");
```

will print the string found at the address `*(esp - 4)`. Thus, if the attacker can manipulate the word below `esp` and then input `%s` to the program, they will be able to read anywhere in memory. \(And using `%n`, they would also be able to anywhere in memory\). The way to prevent format string vulnerabilities is to use `printf` like so:

```c
printf("%s", "/* Get input string from user */");
```

As one may guess, memory exploits are often very brittle \(and specific to certain machines\). Making exploits robust is an art. For instance, in stack smashing, it may be difficult to find the address of the malicious code. To make this robust, the attacker can start the malicious code with 100 NOPs \(so if the address lands anywhere in the "NOP-sled", the attack will still work\).

