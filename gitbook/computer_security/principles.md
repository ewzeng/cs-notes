# Security Principles

Systems are almost surely **not secure** against an attacker with enough resources and money. Thus, we do not ask "is this system secure?" Instead, we ask "is this system secure against those who are willing to attack it?" This is the question of **reasonable security**.

In general, there are three possible ways to defend against attacks:

* Prevention: works great, but can fail hard
* Detection and response: need to worry about false positives \(causes money to respond, crying wolf\) and false negatives \(failure\)
* Defense in depth \(many layers of defense\); best case if detectors are independent
  * Detectors can be composed in parallel or serial \(with different trade-offs in false positives and negatives\)

When designing a system, keep the following in mind:

* Principle of least privilege: give every entity the least amount of privilege needed to complete its job
* Separation of responsibility: try to separate responsibility so no one entity has complete power. For instance \(as an extreme example\), to launch a nuclear missile, some protocols require two people to turn their keys at the same time, so no one person can launch a nuclear missile by themselves.
* Design the system to be modular. This will make it easy to isolate security breaches.
* A **trusted computing base \(TCB\)** is the stuff that **needs** to be secure. Try to make the TCB as small and simple as possible. The TCB should be tamper-resistant, verifiable, and \(when it makes sense\) unbypassable.
  * Often, the TCB is a **reference monitor**: something that controls access control. In this case, we want **complete mediation**. That is, we want every access to go through the reference monitor.
* Do not rely on **security via obscurity**. Hoping that the attacker does not understand the inner workings of a system will not work. If the design of the system gets leaked, one may have to re-design the whole system, which often may not be possible. Instead, design systems under the assumption that the attacker understands every part of it. \(Even better: design systems in the open so other people can provide feedback on how to improve it.\)
  * In fact, the only thing that should be obscure is passwords. This is because passwords are easy to change if leaked, and doing so does not require re-designing the system. \(This is known as **Kerkhoff's principle**.\)

And finally, here are some common principles that are often overlooked:

* Human factors are important! Security systems must be usable \(or people won't use them or will subvert them\). For example, if a company requires passwords to be too complex, people might just write them on a post-it note and stick the note on their desktops.
  * On a related note: we often blame the user for falling for attacks like phishing. However, if users fall for them a lot, we should look into re-designing the user interface.
  * Free advice: use a password manager and two-factor authentication \(because the concept of passwords didn't take into account human factors/usability\)
* Often, the most effective security is to attack the attacker's motivation.
* And don't forget about rubber-hose cryptanalysis. Relevant XKCD: [https://xkcd.com/538/](https://xkcd.com/538/)

