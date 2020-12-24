# Public-Key Storage

Both asymmetric-key encryption and digital signatures require the
ability to correctly obtain the public key of the other party.
However, doing so is not always easy. For example, as we will see in a
later set of notes, communicating to a website server requires knowing
the website's public key. But when we ask for a website's public key,
how do we know it has not been tampered with? Can we be sure there is
no MiTM attacker?

The solution is to use digital certificates. A digital certificate for
a website is the tuple:
$$
(M, \text{sign}(SK_{CA}, M))
$$
where `M` is the message `[Website]'s PK is ... Certificate expiration
date is ...` and `SK_CA` is the secret key of a trusted certificate
authority CA.

Basically, a trusted party (the CA) is vouching for the public key of
a website. The public key of trusted CA's are usually hardcoded in the
browser.

The advantage of using CAs is scalability: CAs can vouch for the
public keys of other CAs, so a browser (like chrome) only needs to
hardcode a few root CAs. Although it is unlikely that the big CA
companies are malicious, security still works best without third
parties. Also CAs can often make mistakes and accidentally vouch for
incorrect public keys. In fact, it can be said that the weakest
vulnerability in internet security are CAs and digital signatures.

