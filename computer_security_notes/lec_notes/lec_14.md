today: DNS (domain name $\rightarrow$ IP)

DNS lookup: we ask resolver (local DNS server) for eecs.berkeley.edu: resolver asks root DNS server. roots directs resolver to .edu DNS server. root asks .edu server, gets directed to berkeley.edu DNS server. and so on. cache heavily for speed.

- a few dozen root DNS servers spread around the world
- backwards hierachy (www.google.com subdomain of google.com!)
- .com server managed by Verisign!

DNS protocol: on UDP.

- ID #: to match query & response, and make it hard for off-path attackers
- question section, answer section (if response)
- if no answer, authority section = ask this guy next. if answer found, authority section = guy who provided answer
- additional section = the guy's IP + other IP addr to cache.

cache poisoning: malicious DNS server puts wrong stuff in additional section about totally unrelated domains. we cache it. soln: don't except additional section stuff unless they're for the domain we're looking up.

old days: ID # was incremented by 1 each time. then attacker could do blind spoofing:

- trick alice to visit bad website. bad website loads image in domain attacker owns. so when alice's brower queries attacker owned DNS, attacker gets alice's ID #
- bad website then loads image from google.com. alice's brower queries. attacker spoofs packet with ID # + 1 and gives alice wrong IP for google.com before the legit response comes

kaminsky blind spoofing attack: bad website loads images from many subdomains X.google.com, so browser queries each one of them. for each X.google.com, spoof a bunch of packets with random IDs. eventually get lucky. in authority section of the spoofs, set google's DNS server to mail.google.com. in additional section, change mail.google.com IP to bad IP.

- take adv that ID #s are 16-bit
- defense: because protocol can't change, can't increase ID size. so randomize src port in IP