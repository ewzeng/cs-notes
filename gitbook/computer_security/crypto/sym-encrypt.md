# Symmetric-Key Encryption

__Symmetric-key encryption__ consists of three functions:

- $$K = \text{Keygen}()$$ generates a key $$K$$
- $$E = \text{Enc(K, M)}$$ encrypts a message $$M$$ with key $$K$$
- $$M = \text{Dec(K, E)}$$ decrypts an encrypted message $$E$$ with key $$K$$

The goal of symmetric-key encryption is hide all information about message $$M$$. That is, an attacker that has the encryption $$E$$ cannot obtain __any__ information about $$M$$ (excepting possibility the length of $$M$$).

As is common in cryptography, we can mathematically define this goal with a __security game__:

1. There are two people: adversary and challenger.
2. Challenger calls $$\text{Keygen}()$$ to get key $$K$$.
3. Adversary queries the challenger for encryptions of all messages of the adversary's choosing.
4. Once ready, the adversary send two messages $$M_1$$, $$M_2$$ of the same length.
5. Challenger sends the encryptions $$E_1$$, $$E_2$$ back. However, the challenger does not tell the adversary which encryption corresponds to which message.
6. The adversary can further query the challenger for encryptions.
7. Once ready, the adversary makes a guess which encryption is which. If the adversary cannot guess correctly with probability $$> \frac{1}{2} + \varepsilon$$, we say the encryption is __IND-CPA secure__.

Notice that any symmetric-key encryption that is IND-CPA secure must be non-determinstic! Otherwise, the adversary could query the challenger for the encryptions of $$M_1$$ and $$M_2$$, and use that to pick the correct guess.

In the next section, we will see how to build a symmetric-key encryption scheme from __block ciphers__.