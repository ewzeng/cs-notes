# DNS

Website names are easier to remember than IP addresses. However, because communication on the internet uses IP addresses, we need a service that translates domain names to IP addresses. This service is called the **Domain Name Service (DNS)**.

To showcase how DNS works, we go through the steps of obtaining the IP address of `eecs.berkeley.edu`.

1. We ask the local DNS server (called the **resolver**) for the IP address of `eecs.berkeley.edu`. The IP address of the local DNS server was given to us when wee first joined the network.
2. The resolver askes a root DNS server (there are a few dozen root DNS servers spread around the world) for the IP address of `eecs.berkeley.edu`.
3. The root server directs the resolver to the `.edu` DNS server. The resolver askes the `.edu` DNS server for the IP address of `eecs.berkeley.edu`.
4. The `.edu` DNS server directs the resolver to the `berkeley.edu` DNS server. The resolver askes the `berkeley.edu` DNS server the same question as before.
5. The `berkeley.edu` DNS server directs the resolver to the `eecs.berkeley.edu` DNS server. The resolver askes the `eecs.berkeley.edu` DNS server for the IP address of `eecs.berkeley.edu`.
6. The `eecs.berkeley.edu` DNS server provides the IP address of `eecs.berkeley.edu` server.
7. The resolver returns the IP address to us.

A few observations:

- There is a backwards hierarchy: `berkeley.edu` is a subdomain of `.edu`.
- The reason we use resolvers instead of querying the DNS servers ourselves is because resolvers can cache heavily for speed.
- DNS servers can (in the **additional section** of the DNS protocol) additionally respond with IP addresses of other domains likely to be visited (for caching).

The DNS lookup is subject to two main attacks:

- **Cache poisoning**: a malicious DNS server can try to put bad IP addresses in the additional section for totally unrelated domains (like `google.com`) which becomes cached. The defense against cache poisoning is to reject any IP addresses in the additional section for unrelated domains.
- Because DNS is done is over UDP, spoofing attacks can also occur. The DNS protocol uses an random ID number to match query and response to make it hard for off-path attackers, but sometimes attacks can still occur (see the **Kaminsky blind spoofing attack**). There is no way to deal with on-path attackers.

In the next section, we will see how to defend against all attacks using a more secure protocol than regular DNS.
