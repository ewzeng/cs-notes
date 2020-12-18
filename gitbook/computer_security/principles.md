# Security Principles

In this section, we present some high-level security principles.

Systems are almost surely __not secure__ against an attacker with enough resources and money. Thus, we do not ask "is this system secure?" Instead, we ask "is this system secure against those who want to attack it?" This is the question of __reasonable security__.

In general, there are three possible ways to defend against attacks:

- Prevention: works great but if it fails, can fail hard
- Detection and response: need to worry about false positive (causes money to respond, cry wolf) and false negative (failure)
- Defense in depth (many layers of defense); best case if detectors are independent
	- Detectors can be composed in parallel or serial (with different trade-offs in false positives and negatives)

When designing a system, keep the following in mind:

- Principle of least privilege: give every entity the least amount of privilege needed to complete its job
- Separation of responsibility: try to separate responsibility so no one entity has complete power. For instance (as an extreme example), to launch a nuclear missile, some protocols require two people turning their keys at the same time, so no one person can launch a nuclear missile by themselves.
- Design the system to be modular. This will make it easy to isolate security breaches.
- A __trusted computing base (TCB)__ is the stuff that __needs__ to be secure. Try to make the TCB as small and simple as possible. The TCB should be tamper-resistant, verificable, and (when it makes sense) unbypassable.
	- Often, the TCB is a __reference monitor__: something that controls access control. In this case, we want __complete mediation__. That is, we want every access to go through the reference monitor.
- Do not rely on __security via obscurity__. Hoping that the attacker does not understand the inner workings of a system will not work. If the design gets leaked, one may have to re-design the whole system, which often may not be possible. Instead, design systems under the assumption that the attacker understands every part of it (even better: design systems in the open so other people can provide feedback on how to improve it).
	- In fact, the only thing that should be obscure are passwords. This is because passwords are easy to change if leaked, and does not require any re-design of the system. (This is known as __Kerkhoff's principle__.)

And finally, here are some common principles that are often overlooked:

- Human factors are important! Security systems must be usable (or people won't use it or will subvert it). For example, if a company requires passwords to be too complex, people might just write it on a post-it note and stick it on their desktops.
	- On a related note: we often blame the user for falling for attacks like phishing. However, if users fall for it a lot, we should look into redeigning the user interface.
	- Free advice: use a password manager and two-factor authetication (because the concept of passwords didn't take into account human factors/usability)
- Often, the most effective security is to attack the attacker's motivation.
- And don't forget about rubber-hose cryptanalysis. Relevant xkcd: https://xkcd.com/538/