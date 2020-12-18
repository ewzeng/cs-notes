##### Semantic Analysis

to annotate declarations: recursively navigate AST (basically draw environment diagrams!)

type: set of values (e.g. fields of a class), and a set of operations on these values (e.g. methods of the class). type checking: operations used with correct types. type soundness: dynamic type always subtype of static subtype. compiler uses static type for type checking.

don't have to always explicitly define types in certain languages if have good type inference rules

type environment: maps identifiers to types