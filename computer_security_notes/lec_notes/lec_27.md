today: more bitcoin

how to users agree on common history? proof of work

in bitcoin, only miners add blocks to blockchain

all miners try to find number such that hash(new block $\|$ rand) has first $N$ bits zero. miners broadcast blocks + proof of work. users then checks the blocks for correctness and accept the longest correct chain

- $N$ is hardcoded into alg for bitcoin (it depends on how long it takes to solve the previous two proof of works)

to make faster, a block contains multiple transactions

if honest miners outnumber malicious miners, proof of work is secure

how to convince people to mine? free coin, transaction fees

bitcoin seems anonymous, but transactions you make leak information

zCash = encrypted versin of bitcoin (the blockchain encrypted)

ledgers have many uses (other than cryptocurrency), like for certificates!