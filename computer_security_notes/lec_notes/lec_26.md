today: building bitcoin

ledger: publicly-visible, append-only, immutable log

assume now there is a trusted ledger owner

each user has PK, SK, referred to by PK

transactions are stored in ledger (assume always in right order)

if alice wants to send money to bob, shes sends and signs (transaction, list of transactions where the money came from) to ledger pwner. ledger owner verifies the transaction + no double counting (needs the list of transactions enrty), and appends to ledger

now, build the ledger

hashchain: each transaction contains hash of previous transaction (so can verify history by getting latest hash)

blockchain: same as before, but use blocks of transactions instead of a single transaction

every participant stores blockchain, when new transaction are broadcast to everyone. but problem: what if blocks are added at the same time? what if malicious users try to fork the blockchain? next lecture!