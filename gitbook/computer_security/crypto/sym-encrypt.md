# Symmetric-Key Encryption

__Symmetric-key encryption__ consists of three functions:

- `K = Keygen()` returns a key `K`
- `E = Enc(K, M)` encrypts a message `M` with key `K`
- `M = Dec(K, E)` decrypts an encrypted message `E` with key `K`

The goal of symmetric-key encryption is hide all information about message `M`. That is, an attacker that has the encryption `E` cannot obtain __any__ information about `M` (excepting possibility the length of `M`).

As is common in cryptography, we can mathematically define this goal with a __security game__:

1. There are two people: adversary and challenger.
2. Challenger calls `Keygen()` to get key `K`.
3. Adversary gets to know the encryption of all messages of their choosing. That is, the adversary sends the challenger a message`M`, the challenger then encrypts `M` with `K`, sends back the encryption `E`, and repeat.
4. Adversary then sends two messages `N_1`, `N_2` of the same length.
5. Challenger sends the encryptions `F_1`, `F_2` back. However, the challenger does not tell the adversary which encryption is which.
6. If the adversary cannot guess which encryption is which with probability $$> \frac{1}{2} + \epsilon$$, we say the encryption is __IND-CPA secure__. Before making their decision, the adversary can keep querying the challenger for more encryptions of any message they choose (i.e. step 3).