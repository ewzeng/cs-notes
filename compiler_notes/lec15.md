##### Handling Functions

need stack, jump and link, calling convention for registers

can have a frame pointer for convenience (so don't have to remember how much to restore stack pointer before return and also can address everything relative to frame pointer), but not necessary

- frame pointer becomes necessary when we have dynamic allocation on the stack (like variable sized arrays)
- frame pointer set and restored by callee (when frame pointer is stored on stack, its called the dynamic link)

in python: have function nesting. to get variables local to the enclosing function, store static link to parent function frame. (basically, we have turned our stack into an environment diagram)

- everytime call a function, pass a static link as a parameter
- alternative solution: use a global display

if no nesting of functions, then a function value (a variable that is a function) is just a pointer. else have to also pass nesting information (i.e. the static link)

- what happens when the frame that a function value points to goes away?  copy the parent frame to the heap and poin the static link to that
  - or not allow this (e.g. can only use a function value as parameters, cannot store in variable)