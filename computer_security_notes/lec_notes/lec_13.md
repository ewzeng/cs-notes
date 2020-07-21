today: TLS (protocol for secure channels). puts the s in https. sits on top of tcp. well designed. provides C.I.A. but not availability

to make RSA do pubkey encrypt, need to add random padding

RSA TLS handshake: 

1. client connects to server, tells server random # $R_B$ and a list of crypto algs
2. server tells client random # $R_A$, algs to use, sends $PK$ and corres certificate from CA. client checks
3. browser constructs $PS$ (premaster secret), sends to server via RSA. $PS, R_B, R_S$ used to generate two pairs of sym/MAC keys. ($R_B, R_S$ used to prevent attacker from recording and replaying msgs to server/browser later as server/browser will using different nonces in different connections)
4. brower and server exchange MACs computed on dialog so far. (this allows each to confirm the other has the right keys and prevents MITM from client to server).
5. done! browser displays green lock. all subseq comm encrypted + MAC'd. sequence #'s included in messages to prevent replay attacks.

D-H TLS handshake: only diff is construct $PS$ with D-H. (server gens random seckey, sends D-H pubkey to client + signs with $PK$)

forward secrecy: if attackers steal secret key of server in future, can they read past convos?

D-H TLS has forward secrecy. RSA TLS does not. (so D-H is used nowadays)

TLS weak point: certificates