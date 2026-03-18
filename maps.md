## Maps 

Conceptually this is a *map* (in certain cases a map is also called a *function*) and has the following properties: It consists of three things, a set of values (*domain*), a rule how to map all of this values, and another set of values (*codomain*) that are the destination of the mapping.

```
X → Y          // Domain X and codomain Y.
x ↦ y = f(x)   // The rule of the map has to be given for every element (i.e. value) of the domain X.
```

It is important to note that the *map as an entity* maps all of its input values (i.e. the elements of the domain) onto the codomain simultaneously; in a way it expresses all of its potential at once. Of course we can always ask it to provide a single result by applying it on one of its values, like `y = f(x)` where y, the result, is a element of the codomain, x is a element of the domain and f represents the rule.

In computing the concept of mapping one type of thing onto another is important on multiple levels of abstraction like a color, a triangle, a three-dimensional object, a level in a game. As we already saw, giving a meaning to a byte of zeros and ones is done by a conceptual mapping, `01100001` means the number `97` but it can also mean the character `'a'`. Considering the number nature of a bit sequence only, the usual representation of a number like `97` is also called a *decimal* representation, `97` is a *decimal number*, the binary representation `01100001` is also called a *binary* representation of the same number, `01100001` is a *binary number*. On another level there is also a mapping between bytes and a instruction the computer should carry out, for example `01100001` maps to the instruction `POPA` which stands for *pop all general-purpose registers* that takes eight values from the *stack* and and puts them into the according registers; the registers are the places where values are stored when they take part in a certain step of computation; the stack is a low-level storage for values. On a higher level we map types of data collections onto other types of structured data, use the address of data as stand-in, and on the highest, mathematical level we map maps on maps that map maps on maps and so forth. In the course of this book we will meet maps in different contexts.

