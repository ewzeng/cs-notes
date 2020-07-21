ROP: return oriented programming (ret2libc, re2esp, ret2eax)

ret2ret is very clever (spmt1 7(h))

integrity of ciphertext: can't tell if the ciphertext was tampered with until we decrypt (so not guaranteed by MAC-then-encrypt)

apparently: hash functions don't need to be collision resistant for pswd hashing, just one-way (but this doesn't make any sense, and hash functions are always collision resistant)

HMAC = a way to turn hash functions into MACs; HMAC is $H(k \oplus opad \| H(k \oplus ipad \| m))$; works as long as opad $\neq$ ipad, even if known

- $H(k\|m)$ not a valid substitute for HMAC due to length-extension attack

reusing key for MAC and enc = not secure

AES is 128-bit cypher (so 16 bytes)

pRNGs: rollback resistant (can't compute what came before)

write-around vulnerabilities can attack stack canaries w/o knowing their values

cannot buffer overflow from heap into stack; to deal with linked lists in heap, can make next point to stack, and then do the exploit next iteration

SHA has a pseudorandom hash property; seems like if add some random bits before applying hash, SHA doesn't leak info

if sym key leaks info within a msg (two blocks in a msg same), then also not IND-CPA

the reason we don't teach RSA as pubkey encrption but as signatures is probably because to implement RSA, need to add some randomness

if mallory can rearrange ciphertext blocks, integrity and authenticity not met