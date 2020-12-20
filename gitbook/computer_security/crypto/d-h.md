# Diffie-Hellman Key Exchange

Communicating with symmetric-key encryption only works if both parties have the same key. Thus, a secure method to agree on a symmetric key is very important. We will look at an algorithm that does exactly this: the **Diffie-Hellman key exchange**.

In the Diffie-Hellman key exchange, there a large prime `p` and value `1 < g < p` that is public.

- Alice picks a secret value `0 < a < p-1` and sends Bob `A = g^a (mod p)`.
- Bob picks a secret value `0 < b < p-1` and sends Alice `B = g^b (mod p)`.
- The agreed-on symmetric key is then `A^b = B^a (mod p)`

The reason Diffie-Hellman is secure is because of the discrete logarithm problem: to find `x` given `g^x (mod p)`, `g`, and `p` is an NP-hard problem.