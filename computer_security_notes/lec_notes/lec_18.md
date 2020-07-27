today: intrusion detection

network intrusion detection (NIDS): scans incoming packets (sit between border router and internal network). has table for all active connections, needs to assemble packets to read (similar to stateful packet filter)

NIDS evasion attack: when you have double parsing, things can be interpreted differently from monitor and end system

- if see RST, can't assume RST is seen by reciever (and clear connection from table)
- complicated to solve (e.g. end system parsing might depend on config files)
- historically, NIDS vs evasion attacks has been a cat and mouse game

NIDS also cannot deal with TLS (encrypted) traffic

host-based intrusion detection (HIDS): installed on end server. less evasion attacks, but less centralized + more expensive

- e.g. system call monitoring, antivirus

log analysis: every night, script runs to analyze log files (cheap, but not real-time)

A = alarm, I = intrusion, then false pos = P(A|not I), false neg = P(not A|I). a good balance between FP, FN depends on context

base rate fallacy: how often attacks occur can make a detector very useful or useless (not just detector sensitivity)

signature-based detection: look for activity that matches structure of known attack

anomaly-based detection: develop model of normal behavior (maybe look at logs), and flag uncommon and rare activity. problem: higher false positives, so susceptible to base rate fallacy

specification-based detection: humans specify model of normal behavior instead of learning

behavioral detection: look for evidence of compromise (e.g. logging is turned off). doesn't detect initial attack but things attackers do after inital attack

antivirus = combo of bunch of techniques (monitoring URLs, scanning network traffic for signatures, queries database for reputation of stuff, sandbox execution, scans file and memory for signatures, runtime analysis of execution behavior, etc.)