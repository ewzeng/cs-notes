AES-EMAC not hash (not collsion-resistant if keys known)

HMAC = MAC + collsion-resistant if attacker has keys

- apply a hash twice (b/c of length extension technicality)

now: asym authenticiy & integrity

digital signature: to verify Alice's msg, need sign(sk_A, M) = sig, verify(pk_A, M, sig)$.

- secure if EU-CPA

ex. of ds is hash then RSA. (RSA can also be used for pubkey encrypt).

- need to hash first for EU-CPA

now: pub key infrastructure

how to get someone's pubkey? mitm attack: "when RSA is taking twice as long as usual" hehehehe

- soln: trusted directory service, certificates

trusted directory maps: to make sure no milm attack with t.d. comm, assume alice know correct pub key of t.d. and t.d. adds ds.

- sign the msg "xxx is bob's pubkey," not just "xxx"
- to prevent replay attack: alice should also send a random nonce and t.d. should sign the msg with "xxx if bob's pubkey, alice's nonce is yyy"