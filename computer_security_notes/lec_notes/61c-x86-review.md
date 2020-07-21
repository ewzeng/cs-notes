this is just to clear up some things that may be confusing.

the addr of a word is the smallest addr of the 4 bytes. that is: the word at 0x0 consists of the bytes with addr 0x0, 0x1, 0x2, 0x3.

little endian means we read the word in reverse order. reason: easy to get the offsets of the word.

esp, ebp (base stack pointer and stack pointer of the current frame), eip (the PC)

for function calls:

- sfp (saved ebp), ofp (old frame pointer), rip (return instruction pointer)
- ofp is where sfp is pointing to (it basically means the same thing as sfp; really a redundant term)



when main calls foo, main pushes arguments and then rip

foo pushes sfp to stack, and then does what it needs to do (possible saving and pushing registers in doing so)

note arguments pushed in reverse order (b/c top of stack is the highest addr)

return value set in %eax