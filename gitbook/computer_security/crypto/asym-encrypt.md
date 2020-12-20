# Asymmetric-Key Encryption

**Asymmetric-key encryption** consists of three functions:

* `PK, SK = Key()` generates a public key `PK` and a secret key `SK`
* `E = Enc(PK, M)` encrypts a message `M` with public key `PK`
* `M = Dec(SK, E)` decrypts an encrypted message `E` with secret key `SK`

The advantage of asymmetric-key encryption is that no key-sharing is needed to communicate. All that is needed to send an encrypted message to someone is their public key `PK`. However, as only the recipient has `SK`, only the recipient can decrypt the message.

We say that an asymmetric-key encryption scheme is IND-CPA secure if attackers cannot distinguish between the encryptions of two equal length messages of their choosing. The security game corresponding to this definition is the same as the security game for symmetric-key encryption schemes, except there is no query phase \(as the adversary can encrypt messages themself\).

Two popular asymmetric-key encryption schemes are El Gamal and RSA. These two encryption schemes are IND-CPA secure assuming the discrete logarithm and prime factorization are NP-hard problems, respectively. We will go over El Gamal because it is conceptually simpler and carries parallels with Diffie-Hellman. \(Remark: regular RSA taught in number theory classes is deterministic. To make RSA IND-CPA not deterministic, one must introduce some tweaks.\)

## El Gamal Public Key Encryption

In El Gamal public-key encryption, there is a large public prime `p` shared by everyone.

To generate keys, do the following:

* Pick `1 < g < p` and `1 < SK < p-1`. `SK` will be the secret key. 
* The public key will be the pair `PK = (g^SK mod p, g)`

El Gamal then works like this:

* To encrypt message `0 < M < p`, pick a random `0 < R < p`. Get `PK = (g^SK mod p, g)` of the recipient. Then the ciphertext is the pair `E = (g^R mod p, m * PK^R mod p)`
* To decrypt, notice that `(g^R)^SK = PK^R mod p`. Do a \(modulo\) division to get `m`.

## Hybrid Encryption

Because asymmetric-key encryption is a lot slower than symmetric-key encryption, people often use asymmetric-key encryption to send a symmetric key `K`, and then use symmetric-key encryption with `K` to communicate.

This **hybrid encryption** method usually used when Diffie-Hellman is not applicable, i.e. when the reciever is not online at the moment \(D-H requries both parties to be online as the shared symmetric key is determined with inputs from both parties\).

