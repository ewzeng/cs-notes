today: DNSSEC

how to make DNS secure? DNS over TLS too slow, doesn't stop cache poisoning, need to trust resolver. better idea: signatures!

DNSSEC:

- hardcode pubkey of root DNS server
- when query DNS server, response will include next DNS server's pubkey. the server will also sign response
- if name $n$ not found in domain, DNS server should respond with the two valid names that $n$ lies in between (alphabetical order) and sign it. (this way, server can precompute all signatures it might need to send, and not have to sign on the fly)
- resolver returns appropriate responses + signatures

DNSSEC weakness: partial deployment