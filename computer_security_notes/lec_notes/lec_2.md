today: security principles (high level)

often we blame the user (for things like phishing)

- if users fall for it alot, we should redesign the system/interface

cost-benefit analysis ubiquituous security: how much to spend on security? how much are attackers willing to spend to attack me?

possible countermeasures:

- prevention (preventing all bad things): works great but if fails, can fail hard
- detection and response; need to worry about false positive (causes money to respond, cry wolf) and false negative (failure)
- defense in depth (many layers of defense); best case if detectors independent
  - parallel vs serial composition (trade offs in false pos/neg)

free advice: use password manager and two-factor authentication (b/c the passwords stuff didn't take into account human factors/usability)

in the world of safes: security measured by how long it takes an expert with certain tools to break-in (this again emphasizes "reasonable security")

rubber-hose cryptanalysis: https://xkcd.com/538/

principle of least privilege; separation of responsibility (so no one thing has complete power)

trusted computing base (tcb): stuff thats needs to be secure; try to make tcb as small and simple as possible

- should be tamper-resistant, verifiable, and (when it makes sense) unbypassable

reference monitor: controls access control (a tcb); want complete mediation (every access goes thru reference monitor)

modular design: can lead to isolation of security breaches (closely related to privilege separation)

more security principles: fail-safe defaults, only secure as the weakest link, don't rely on security thru obscurity, proactively study attacks, trusted path (how do I know I'm interacting with the real thing? need something trusted)

kerkhoff's principle (only thing that should be obscure is the pswd; don't do security via obscurity!)

TOCCTOU: time of check to time of use attack (DOA exploit!)