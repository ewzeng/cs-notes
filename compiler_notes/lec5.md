##### More Parser

AST can be seen as the extracted "essence" of the parse tree. note: lisp programs are already ASTs!

now that we know how a parser works abstractly (token $\rightarrow$ parse tree $\rightarrow$ abstract syntax tree), lets consider implementation. (note, in most implementations, we don't create a parse tree, but the underlying actions are equivalent to doing so)

problem: BNF grammar $\rightarrow$ parser. solution: a recursive-descent program. given a set of rules, can systematically create such a program pretty easily (incorporate FIRST and FOLLOW functions for a even more systematic approach)

- LL(1) means only need to check 1 symbol of input ahead to see which branch to take
- if LL(1), can simplify the parser even more with a table lookup

