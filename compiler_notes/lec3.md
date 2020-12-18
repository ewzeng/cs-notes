backus-naur form is an alternate to using regex (another way to describe languages). can describe all regex languages, and more

- key: BNF describes the smallest language that satisfies all the rules

how to write code that recognizes a language:

- regex $\rightarrow$ nfa $\rightarrow$ dfa $\rightarrow$ code
- all regex can be converted into nfa (a recursive construction of the nfa)
- all nfa can be turned into dfa pretty easily, but often nfa form much more clear conceptually
- easy to convert dfa to code

in jlex and flex implementation, when dealing with a list of regex patterns, each corresponding to a type of a token, we use two rules to determine which token type to return:

- maximum munch (choose the pattern that matches the longest)
- if tie, choose first pattern that comes in the list

