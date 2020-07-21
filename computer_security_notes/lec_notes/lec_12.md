link-layer threats: eavesdropping, injecting packets (spoofing)

internet-layer spoofing: much easier if on-path (eavesdrop TCP seq #)

- race condition between victum & adv: TCP disgards packets with same seq #

attackers can also inject RST packets to terminate connections (Great Firewall does this)

in old days, off-path attackers could do blind spoofing:

- servers used to choose seq # based on local clock

- so if server saves IP addr to avoid re-authentication, adv can use that IP to est connection. then guess server's seq # (may need to hurry because real client will recieve stuff and may send RST)

DHCP server: gives you an IP addr, DNS server IP, gateway router (hapens when you first connect to a LAN)

DHCP attacks: race real DHCP server to give bad DNS server, gateway router

- hard to prevent w/o some trust anchor
- similar attacks work on other broadcast protocols

MITM = on-path + can change data