##### Exceptions

many different approaches

non-standard return: compiler puts j ERROR_HANDLER after every jal instruction. to throw exception, put type of exception in some standard register and return using jr ra.  normal return is jr ra, 4.

C uses stack manipulation with setjmp, longjmp.

java uses PC tables: a table that maps instruction addr to exception handlers (i.e. run this handler if something goes wrong with this instruction) and contains info on how to return from a function to caller when exception is thrown. to throw exception, do a recursive table lookup to find correct exception handler (lookup curr inst, if not found then lookup the calling inst invoking curr function, etc)

##### OOP

problem: overriding methods of parent classes

fully dynamic approach: have a dictionary for each class and instance. create an instance by copying the class's dictionary. check for value of attribute in object's dictionary, then in class, then superclass, etc. (somewhat like environment diagrams)

straight single inheritance: each class has a data structure mapping method names to functions, variable names to offsets, and a pointer to superclass. each instance has a pointer to the corresponding class data structure.

single inheritance with static types: similar data structure as before, but put entries for all methods (not just the overidden methods) in the data structure. insist all possible overridings are type compatible.

- in C++, this data structure is called a vtable
- key: offsets of variables in instances and method pointers are same for all subtypes

java complicates things with interface types. solution: add another level of indirection

full multiple inheritance of C++: even more complicated (multiple vtables)