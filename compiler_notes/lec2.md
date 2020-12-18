##### Lexical Analysis

source code $\rightarrow$ tokens

token: syntactic category (some "type") + semantic information (the "value"). parser (which comes after lexical analysis) only needs syntactic category to create the syntax tree

to do lexical analysis, we will need to know regex

classical regex:

- expression $R$ denotes a language $L(R)$ (i.e. a set of string)
- use a few recursive rules to define
- often use abbreviations (e.g. the dot is expression containing everything but the next line character, character lists)

there are some extensions to regex that provide additional features (like lazy matching), often for particular applications (match only beginning of line in text file)

once have regex, easy to write a lexer