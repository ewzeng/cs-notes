##### Bottom-up Parsing

recursive decent is great, but we can come up with a different method (idea: build the parse tree bottom up)

so: earley's algorithm (for context-free grammars)

- fix string $S = c_1c_2\dots c_n$
- define a recursive function $parse(S, \alpha \cdot \beta, s, k)$. the dot $\cdot$ is intuitively the current parse position of rule $\alpha \beta$
- apply memoization
- works with ambiguous grammars; can incorporate semantic values (and thus build AST)