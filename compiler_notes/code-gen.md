# Assembly Code Generation

The last stage of the compilation process is converting an annotated AST into assembly code. This is usually done in two steps:

1. Generate intermediate (machine) language (IL) for a virtual machine
2. Turn IL to real assembly

Reasons for separating the process into two steps instead of directly producing machine language:

- When generating IL, don't have to worry certain limitations (see three-address code virtual machine below)
- Can target different architectures by swapping out the second step

To perform step 1, have to specify what virtual machine we use as a target. Common possibilities:

- Stack machine: no registers, everything is a stack.
- Three-address code: infinite supply of registers. All IL instructions look like: `target := operand [operator] operand`. We will be using 3AC here.

Generating IL for 3AC can be broken down into sub-steps: first generate IL, and then optimize.

Turning 3AC IL into assembly is mainly a question of efficient register allocation + fiddling with stack.

## IL Generation

It is straightforward to generate 3AC IL code from an AST (the infinite register abstraction is incredibly helpful). [Include some examples here]

## IL Optimization

Once assembly code has been generated, optimize it. Many different optimizations, each do very little, but can repeatedly apply them (as performing one optimization can enable others).

Terminology:

- Basic block: a maximal sequence of instructions with no labels (except first instruction) or jumps (except for last instruction). Can be thought as an "atomic" block of instructions.
- A function can be represented as a directed graph of basic blocks representing the possible flow of execution (control-flow graph)

Two main types of optimization. Local optimization = apply to a basic block. Global optimization = apply to control-flow graph of a function

### Local Optimizations

- Algebraic simplification: `x1 := x1 + 0` can be deleted
- Constant folding: operations on constants can be computed at compile time
- Eliminate unreachable code
- If put code into single-assignment form (don't assign to a register twice), can do even more optimizations:
  - Common subexpression elimination: if `x1 := x2 + x3` appears, can replace all subsequent `x2 + x3` with `x1`
  - Copy propagation: if `x1 := x2` appears, can replace all subsequent `x1` with `x2 ` (doesn't optimize directly, but may enable other optimizations)
  - Dead code elimination: assignment statement to a register not used (before reassignment) can be deleted
  - Note: can do single-assignment form between 3AC has infinite registers

### Global Optimizations

Global flow analysis:

- Trace through control-flow graph to best deduce information for certain registers at certain points (implementation: apply a deduction algorithm repeatedly until get a fixed state), and use this information to apply optimizations
  - If information = value of register (corresponding optimization = constant folding)
  - If information = register is live/dead (corresponding optimization = dead code elimination)

## 3AC IL to Assembly (i.e. Register Allocation)

If represent each virtual register as a node and draw a line between two nodes if the corresponding virtual registers are both live at some point, then a coloring of the resulting graph represents a valid register allocation (each color represents a real register).

- Use global flow analysis (described previously) to decide if a register is live/dead at a certain point

However, finding minimal colorings of graphs in NP-hard, so use some heuristics to get a good coloring. If not enough real registers, spill to the stack.

Other things to consider in this step of compilation:

- Function prologue/epilogue may need to be tweaked (because it depends on register usage).

- Cache optimizations can be implemented (however, this is difficult)