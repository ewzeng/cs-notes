##### Deterministic Bottom-up Parsing

earley's algorithm has high overhead (even though $\mathcal O(n)$); if grammar deterministic, can use LR parsing instead

divide input string into $\alpha \beta \gamma$, where $\alpha \beta$ is the handle, $\gamma$ is the unprocessed string

- two possible moves: shift (take a character from the unprocessed string and add to the handle) and reduce (replace $\beta$ with LHS of some rule)
- handle also referred to as a stack (shift = push to stack; reduce = pop stuff off stack and push corresponding symbol on stack)
- use a DFA to decide whether to shift or reduce (build a regular BNF $\rightarrow$ NFA $\rightarrow$ DFA, or do something similar to earley's alg)