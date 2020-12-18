The log/journal is on disk. Once changes applied, safe to remove entries in log. Transaction not executed unless commit is pushed. User only notified until commit pushed.

- Thus everything is written twice.

Assumption: updates to sectors atomic

Log structure file system: log is what is recorded (i.e. only write things once). Replay log logically to get result if crash. In other words, do only sequential writes (so write fast). Used by flash file system because random reads is fast.

With flash, people use a different point of view than disk.

Distributed systems require very careful design. (Client-server is an example of a centralized system)

Protocol: agree of how to communicate, like syntax, etc. Described by state machines.

IP (internet protocol) is the narrow waist.

High influential paper: End-to-End Arguments in System Design.

- End to end solution to reliable file transfer: end-to-end checksums and try again if necessary (not make each step reliable)
- So philosophy: think again before implementing functionality in the network.

Interface for E2E: send(message, mbox), recieve(message, mbox)

Distributed consensus making: all nodes trying to make a decision - same may crash. And need to not forget data.

General's Paradox - coordinating attacks. (Named after custer). Can't solve, but can solve a related problem with a two-phase commit. 2PC Algorithm.