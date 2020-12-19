block cipher E(K, M) $\rightarrow$ C; M and C same length; a permutation

block cipher secure if attackers cannot differentiate between E(K, _) and rand perm. this can also be expressed as a game

when we say attackers, we assume efficient attackers (i.e. with algs that run in polynomial time). e.g. not brute force factoring in RSA

block cipher standard: AES (believed to be a secure block cipher)

no one has proved any block cipher to be secure (either would probably lead to a proof of P!=NP)

need to use block ciphers in an IND-CPA secure way 

- naive scheme (ECB mode) deterministic; bad
- CBC mode: use previous ciphertext block as initialization vector (IV); first IV rand gen and appended at the beginning of ciphertext; can prove block cipher secure $\implies$ CBC is IND-CPA secure
- CTR mode: generate nonce N, XOR m-th block with E(K, N|m); append N to beginning of ciphertext; (N doesn't have to be rand, just has to differ from msg to msg)

if msg not multiple of 128: padding (but be careful!)

- one way is to always pad with 10...0 (and if we are multiple of 128, add an extra block of 10...0)

IND-CPA guarantees even if part of plaintext is known, still can't decrypt the rest

pseudo-rand generator:

- input seed short (say 128 bits, get seed from some environment variables); output huge number of bits (millions)
- secure pseudo-rand: attacker can't tell if its random or pseudorandom (can define another game)
- steam cypher: xor with output of PRG (maybe add an IV for nondeterminism); super similar to OTP, CTR