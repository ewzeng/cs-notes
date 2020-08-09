today: internet anonymity (hard if you are not allowed to hack other machines, i.e. a good guy)

proxy: intermediary that relays our traffic. basic idea: alice sends enc(bob, msg) to proxy. proxy decrypts and sends msg to bob

- cool fact: VPNs were not designed for anonymity! (see lecture on firewalls). but they are basically proxies
- problem: proxy has to be trusted

onion routing: use multiple proxies (key: good as long as one proxy is good)

- say C, D are proxies. alice sends enc_Ckey(enc_Dkey(msg, bob), D) to C. each proxy can only peel off one layer of the encryption, and no proxy knows both the sender and reciever
- TOR is the state-of-the-art onion routing implementation
- slight catch: if all other proxies but one are colluding, and the good proxy has very little traffic, the even if we use that good proxy, the other proxies can try to match the input/outputs of the good proxy

internet censorship: find/setup servers that large amounts of traffic pass through, and use blacklist + signatures (basically NIDS). much easier to block traffic than trace

on-path censors: set up stuff at ISP, get a copy of every packet. set rst injection if contains blacklisted signature

to evade censors: encryption! but still can't get to blocked IPs, and gov't can ban encrypted traffic (block TLS, ban encryption software). leads to a cat and mouse game (people try to hide they are encrypting, gov't updates software to find out).

TOR is the defacto standard for censorship resistance