td drawbacks: scalability, central point of attack, difficult to recover from failure, always has to be running

digital certificate: alternative to td

- certificate = sign($SK_{CA}$, "Bob's PK is 0x...", "expiration xxx"); assume browsers have $PK_{CA}$ hardcoded
- main advantage: can get certificate from other ppl, don't need to always ask CA
- chains: CA certifies other CA, which certifies next CA, etc. so one CA doesn't have to know everyone's pubkey
- to revoke, can use revocation lists (not great, some browsers may not check often); soln to CAs being decieved is blockchains

now: passwords

servers should store pswds as hashes

but if hashes stolen, offline password guessing (e.g. dictionary attack) is effective. cool: dictionary of $2^{20}$ can guess 50% of passwords

- use salts to prevent attackers precomputing hashes and doing a lookup. also use slow hashes (e.g. hash multiple times)

