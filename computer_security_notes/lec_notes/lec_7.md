asym crypt, pub key, secret key

one-way functions: $x \rightarrow$ f(x) easy, hard to find any $x$ s.t. $f(x) = y$ for given $y$ (no poly-time alg). e.g. block cipher

- can't prove any function is one-way else P!=NP

famous one-way function: discrete-log

- $f(x) = g^x \mod p$ where $p$ is large prime (2048 bits), $g$ some value in $[2, p-1]$

Diffie-Hellman Key exchange: how to agree on a symmetric key

- public large prime $p$, $1 < g < p$
- alice picks secret key $a$ from $[1, p-2]$; alice pub key: $A = g^a \mod p$; same for bob
- $A^b = B^a = g^{ab} \mod p$; this is their secret sym key

d-h not secure with malice (MiTM). many ways to solve (like certificates). a simple solution is to send a digest over a different channel (like physical access), but this isn't always appropriate.

public-key encryption (don't need to determine a sym key to continue communicating)

- semantic security game: IND-CPA but no query phase (since attacker can encrypt stuff himself)

el-gamal pubkey encryption:

- rand gen: large prime $p$, $g \in [2, p-1]$, secret key $k \in [2, p-2]$
- publish pub key $= g^k \mod p$ and $g$
- to send msg $m \in [1, p-1]$: pick rand $r \in [1, p-1]$. get pubkey $pk$ and $g$ of recipient. then ciphertext c = ($g^r \mod p$; $m \cdot pk^r \mod p$)
- decrypt by noticing $(g^r)^k = pk^r$