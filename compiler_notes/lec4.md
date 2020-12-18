##### Parser Introduction

a string $T$ is in a language (decribed by BNF grammar $G$) if there is a **derivation** of $T$ from the start symbol of $G$

- to do this, provide a sequence of sentential forms. at each step, apply one of the rules of $G$
- doesn't matter which order you apply the rules (context-free). but can apply the rules in a certain order (e.g. leftmost derivation or rightmost derivation)
- equivalently, can draw a parse tree

if some strings have two different parse trees, then the grammar is ambiguous. (each parse tree corresponds to one interpretation of the string)

can set semantic values to each node on parse tree; computed by going leaves up. finally get a semantic value for the root node.

- these semantic values don't have to be numbers, can also be trees. this is how we create an abtract syntax tree!