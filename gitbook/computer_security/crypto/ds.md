# Digital Signatures

Symmetric-key encryption is to asymmetric-key encryption what MACs are to __digital signatures__. That is, a digital signature consists of three functions:

- `PK, SK = Key()` generates a public key `PK` and a secret key `SK`
- `S = Sign(SK, M)` signs a message `M` with the the secret key `SK`. The signature is a fixed length bit string.
- `Verify(PK, S, M)` verifies that `S = Sign(SK, M)`

In other words, digital signatures can provide integrity and authenticity even if the communicating parties do not share the same key.

We say that a digital signature scheme is secure if a (polynomial-time) attacker cannot forge a signature of any message of their choosing without the secret key `SK`. This can be expressed in a security game similar to the one for MACs.

One way to produce a secure digital signature is to first hash the message, and then apply regular RSA.