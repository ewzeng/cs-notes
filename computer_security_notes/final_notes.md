CSRF can work with HTTP GET requests as well (parameters in URL), but good servers only update sensitive data with HTTP POST requests

DNSSEC: for non-existent domains, have NSEC and NSEC3 policies. NSEC3 more overhead, but prevents zone-walking. in NSEC, return pair (first, last) if before or after all domain names

session cookies are stored in a backend database table, can SQL injection

in the security games, we assume adversity knows the (encryption/signature) schemes of the challenger, but not the keys

TLS does not hide IP

false positive = prob(flagged given harmless). false negative = prob(not flagged given malicious)

to trick someone to go to URL (or mount CRSF attack), can do <code><img src="URL"></code>, or <code><script>window.location="URL"</script></code>

origin header: where fetch **originated** from; referer header: previous web page (origin header goes further back)

in D-H TLS, private key is used for signature, not encryption

padding oracle attack is one reason we prefer encrypt-then-MAC, not MAC-then-encrypt

TOR's weakness: timing attacks

collision resistance implies second preimage resistant