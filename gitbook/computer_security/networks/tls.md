# TLS

One day to defend against on-path attackers is to use **TLS**. TLS is
a well-designed protocol that sits on top of TCP, and is the gold
standard for establishing secure channels.

* TLS with `http` is `https`.
* When TLS is used, chrome shows a lock icon in the URL bar.

## How TLS Works

Assume client **A** wants to communicate to server **B** using
TLS. **A** will first create a TCP connection with **B**. Then over
the TCP connection, the following occurs:

1. **A** tells the server a random number `R_A` and and list of cryptography algorithms **A** supports.
2. **B** tells **A** a random number `R_B`, an algorithm to use, **B**'s public key `PK`, and a certificate to verify `PK`. **A** verifies everything.
3. **A** constructs the premaster secret `PS` and sends `PS` to **B** using El Gamal (or RSA) encryption with `PK`. The number `PK`, `R_A` and `R_S` are used to generate two pairs of symmetric encryption and MAC keys (based on the algorithm chosen earlier).
4. **A** and **B** exchange MACs computer on the dialog so far. This allows each to confirm the other has the right keys, and makes sure there is no MITM attacker.
5. All subsequent communication is encrypted and MAC'ed with the keys generated. Sequence #'s are included in messages to prevent replay attacks.

## Observations

TLS ensures that **A** knows she is talking to **B** without any MITM
attacker, and thus any possibility of an on-path attack. With TLS,
however, **B** does not who he is talking to: all **B** knows is that
he is talking to someone. But as **B** is the server, **B** doesn't
really care.

* If **B** needs to identify the user of **A** (say **B** is a web server that stores sensitive information), then **B** could make the user of **A** login to an account.

The reason `R_A` and `R_B` are used is to prevent attackers from
recording and replaying messages to either the server or the computer
at a later time (as the server or computer will be using different
nonces in different connections).