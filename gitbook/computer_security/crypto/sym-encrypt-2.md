# Symmetric-Key Encryption II

The most common IND-CPA secure symmetric-key encryption schemes are built with **block ciphers**.

## Block Ciphers

A block cipher consists of two functions:

* $$E = \text{Enc}(K, M)$$, where $$K$$ is $$k$$-bits, and $$E$$ and $$M$$ are both $$n$$-bits \($$n$$ is the **block size**\)
* $$K = \text{Dec}(K, E)$$, the inverse function of $$\text{Enc}$$

In other words, a block cipher is a key-dependent permutation on $$n$$-bit messages. We say that a block cipher is secure if an attacker cannot differentiable between $$\text{Enc}(K, \_)$$ for a randomly chosen $$K$$ and a random permutation. Like before, this can be expressed more formally with a security game.

No one has ever proven any block cipher to be secure \(if fact, such a proof would probably lead to a proof of P!=NP\). However, we can try our best to create one. In the 2000s, the US Government organized a competition for the best block ciphers designs. Of the fifteen designs, the block cipher **AES** was chosen. AES is still the block cipher standard and is believed to be secure.

* Professor Wagner, who often teaches CS161, developed the TwoFish block cipher that was a finalist in this block cipher competition.

## Using Block Ciphers for Symmetric-Key Encryption

Let's build an IND-CPA secure symmetric encryption scheme. For simplicity, we will use the simplest version of AES which has 128-bit keys and a 128-bit block size. Suppose we want to encrypt a message $$M$$ whose length is a multiple of 128. How do we do this?

### AES-ECB

The simplest way would be to randomly choose a $$k$$-bit string and let that be the key $$K$$. To encrypt, we chunk $$M$$ into 128-bit blocks, and to each block, apply $$\text{Enc}(K, \_)$$. To decrypt, we do the same thing, but with $$\text{Dec}(K, \_)$$.

However, the symmetric encryption produced would be deterministic, which means it would not be IND-CPA. We will need to do better than this.

### AES-CTR

In AES-CTR, we chose $$K$$ as before, but we also chose a random 64-bit string $$N$$ \(called the **nonce**\). To encrypt, we chunk $$M$$ into 128-bit blocks, and XOR the $$m$$-th block with $$\text{Enc}(K, N | m)$$. That is, we represent $$m$$ as a 64-bit string, concatenate $$N$$ with $$m$$, apply AES to the resulting string, and XOR the result with the $$m$$-block. Then we append $$N$$ to the beginning of our message.

To decrypt, we remove the nonce $$N$$ from the beginning of the message and then use $$N$$ and key $$K$$ to undo the XOR. \(More specifically, we once again XOR the $$m$$-th block with $$\text{Enc}(K, N | m)$$. Double XORs cancel each other out.\)

* Assuming AES is secure, we can prove AES-CTR is IND-CPA secure \(not too difficult: proof by contradiction\)
* The nonce $$N$$ actually does not have to be random, as long as it differs from message to message.
* It is assumed that $$m$$ can be represented as a 64-bit integer. For most practical purposes, this is enough.

### Padding

What if the message $$M$$ is not a multiple of 128-bits? The solution is to pad $$M$$ with bits to make it a multiple of 128.

* One way is to always pad with 10...0 \(and if the message is a multiple of 128, add an extra block of 10...0\).

## More Uses of Block Ciphers

### Pseudo-Random Generators

A pseudo-random generator is a generator that takes a short random input seed \(say 256 bits\) and outputs a huge number of pseudorandom bits \(usually millions\). We say a pseudo-random generator is secure if an attacker cannot differentiate between a pseudorandom sequence and an actual random sequence \(once again, we can define a security game to make this rigorous\).

We can create a secure pseudo-random generator by using the first half of the input seed as the key $$K$$ and the second half as the nonce $$N$$, and then creating the stream:

$$
\text{Enc}(K, N | 1) | \text{Enc}(K, N | 2) | \dots
$$

From this perspective, AES-CTR can be seen as XOR-ing a message with a pseudo-random sequence created in this manner \(i.e. AES-CTR can be seen as a **one-time pad**\).

## Randomness

How do we generate random keys for AES? It happens that we do not need true randomness; a secure pseudo-random generator is enough to guarantee IND-CPA \(not a difficult proof\). However, using pesudo-random generators requires a short random input seed. How does a computer find this randomness?

The answer is the environment.

* The computer uses variables from the environment to derive the input seed. Examples include the time the computer was booted up, network packet timing, CPU temperature, etc.

