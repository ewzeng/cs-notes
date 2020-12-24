# Public-Key Storage

Both asymmetric-key encryption and digital signatures requires the
ability to correctly obtain the public key of the other party.
However, doing so is not always easy.

For example, as we will see in a later set of notes, communicating to
a website server requires knowing the website's public key. But when
we ask for a website's public key, how do we know it has not been
tampered with?

The solution is to use digital certificates. A digital certificate for
a website is the tuple:
```
(M, sign(SKCA, M)
```
where `M` is the message `[Website]'s PK is ... Certificate expiration
date is ...` and `SKCA` is the secret key of a trusted certificate
authority CA.

Basically, a trusted party is vouching for the public key of a
website. The public key of trusted CA's are usually hardcoded in the
browser.

The advantage of using CAs is scalability: CAs can vouch for the
public keys of other CAs, so a browser (like chrome) only need to
hardcode a few root CAs.

The disadvantage of using CAs is the trust factor. Although it is
unlikely that the big CA companies are malicious, security still works
best without a third party. Also CAs can often make mistakes, and
accidentally vouch for incorrect public keys. In fact, it can be said
that the weakest vulnerability in internet security are CAs.

