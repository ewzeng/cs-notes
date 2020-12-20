# Hash Functions

We have seen how cryptography can be used to ensure confidentiality of messages. Now we will look at how cryptography can ensure integrity and authenticity of messages.

- __Integrity__: a message has not been tampered with
- __Authenticity__: a message has not been tampered with and the author of the message can be verified

But before we get into integrity and authenticity, we first must discuss hash functions.

## Cryptographic Hash Functions

A __cryptographic hash function__ is deterministic and unkeyed function `H` that takes in an arbitrary length bit-string and outputs a fixed length bit-string. For instance, the SHA256 hash algorithm can be used to hash a message of any size, and produces a 256-bit hash value.

Cryptographic hash functions have two important properties:

- __Preimage Resistant__: for randomly chosen `X`, it is infeasible to find a message `M` such that `H(M) = X`
- __Collison Resistant__: it is unfeasible to find any pair of distinct messages `M`, `N` such that `H(M) = H(N)`

Because of these properties, hash functions are incredibly useful and have many different applications.

## Integrity

Cryptographic hash functions can acertain the integrity of a message. If Alice wants to send message `M` to Bob, she could also send the hash of the message `H(M)`. Upon recieving the message, Bob can compute the hash of `M` to verify the message has not been corrupted in transmission.

However, hash functions do not guarantee authenticity. Because anyone can use a hash function, Bob has no way of knowing that it was really Alice who sent the message `M`.

In the next section, we will see that one can do better.