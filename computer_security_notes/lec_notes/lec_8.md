hybrid encryption: use pub key encryption to send sym key

- use hybrid encryption instead of d-h if reciever not online at the moment (like email)

need slighter stronger than discrete log hardness to prove el gamal secure

el gamal: a combo of d-h and OTP (but mod mult instead of XOR). idea: generate a different OTP key for each exchange. use d-h to agree on OTP key.

now let's look at integrity & authenticity

cyptographic hash function: $\{0,1\}^* \rightarrow \{0,1\}^L$, deterministic. sha256 $\implies$ L = 256. secure if:

- one-way (for rand $X$, adv has $\varepsilon$ probability finding an elem of $H^{-1}(X)$)
- collision-resistance (infeasible to find $X, X'$ s.t. $H(X)=H(X')$). no collisions found for sha256 yet.

hashes guarantee integrity but not authenticity

MAC: takes a key and message to produce checksum. secure if EU-CPA: after queries, adv should not be able to come up with the MAC of a msg not queried before.

AES-EMAC (a MAC with AES): choose rand key  $k = (k_1, k_2)$, split msg into 128-bit blocks, chain mode with $k_1$, and put thru AES with $k_2$. the last step is needed or else not EU-CPA.

best sym practice: encrypt, and also send MAC of encryption

- used diff keys for encryption (b/c security of encryption and MAC proven independently, interplay not considered)
- MAC leaks partial info (not IND-CPA), so don't MAC plaintext, just encryption