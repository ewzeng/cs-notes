LALR(1): a subset of LR(1) that we can apply efficiency hack (collaspe lookup table)

to resolve shift-reduce conflicts: provide information about precedence/associativity. default is to choose shift.

reduce-reduce conflict: messer, often serious problem with grammar

to recover from parsing error: bison/cup use a special error token