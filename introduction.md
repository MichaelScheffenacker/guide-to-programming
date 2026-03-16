# Introduction
It is dangerous to program. A beast is easily created that is going to devour the programmer.
Of all techniques programming is the easiest to create elements. Therefore elements are swiftly connected to systems, growing more and more complex, and soon becoming incalculable [unueberschaubar: multitudinous].
Since most technical disciplines are bound to the real world [Diesseits] they require a great effort to sustain the impassabilities of physics. They might have to fit measurement tolerances and material specifications, means of transportation the burden to replicate all the effort to make a second copy of the same thing. *For my final project at school I had been in the workshop once to build a part on the lathe that had to have a press fit. At the first try I took off too much and it came out too small. Then I had to lathe the entire part again and when I came back to to the diameter of the press fit I [zugestellt] the tool less than the dial was showing. But it still came out too small.* The digital computer frees us from the physical world and allows to operate on the realm of ideas. This allows to create elements that follow the specification completely; in fact the specification and the creation of an element are virtually the same.

---

It is widely known, that computers are working with zeros and ones, but to most it remains a mystery how it is possible to navigate virtual worlds on a screen, to edit text over the internet, make complex scientific calculations or to train machine learning models that seem to be conversing with us almost like another human being, by using nothing else but zeros and ones. 

A computer stores the information, the *data* it is working on, in *memory*. The memory is a long list of zeros and ones that is sectioned in clusters of eight. A single digit in this long list is called a *bit* a sequence of 8 bits is called a *byte*, e.g. `00001111`. A longer series of bits that is processed in one chunk is called a *word*, like 16-, 32-, 64-bit words; for larger amounts of data SI prefixes like kilo, mega, giga, terra are used, like gigabit per second (Gb/s) internet or a harddisk with 12 terrabyte (12 TB) of storage capacity. The zero and the one are the alphabet `{0, 1}` of the computer and this alphabet is used to generate all other symbols needed. Any sequence of bits can be interpreted as a number, the representation of zeros and ones of this number is also called a *binary number*.

```
'a' = 01100001
'A' = 01000001
'z' = 01111010
97  = 01100001
3.1415 = 01000000010010010000111001010110
true  = 1
false = 0
```

Conceptually this is a *map* (in certain cases a map is also called a *function*) and has the following properties: It consists of three things, a set of values (*domain*), a rule how to map all of this values, and another set of values (*codomain*) that are the destination of the mapping.

```
X → Y          // Domain X and codomain Y.
x ↦ y = f(x)   // The rule of the map has to be given for every element (i.e. value) of the domain X.
```

It is important to note that the *map as an entity* maps all of its input values (i.e. the elements of the domain) onto the codomain simultaneously; in a way it expresses all of its potential at once. Of course we can always ask it to provide a single result by applying it on one of its values, like `y = f(x)` where y, the result, is a element of the codomain, x is a element of the domain and f represents the rule.

In computing the concept of mapping one type of thing onto another is important on multiple levels of abstraction like a color, a triangle, a three-dimensional object, a level in a game. As we already saw, giving a meaning to a byte of zeros and ones is done by a conceptual mapping, `01100001` means the number `97` but it can also mean the character `'a'`. Considering the number nature of a bit sequence only, the usual representation of a number like `97` is also called a *decimal* representation, `97` is a *decimal number*, the binary representation `01100001` is also called a *binary* representation of the same number, `01100001` is a *binary number*. On another level there is also a mapping between bytes and a instruction the computer should carry out, for example `01100001` maps to the instruction `POPA` which stands for *pop all general-purpose registers* that takes eight values from the *stack* and and puts them into the according registers; the registers are the places where values are stored when they take part in a certain step of computation; the stack is a low-level storage for values. On a higher level we map types of data collections onto other types of structured data, use the address of data as stand-in, and on the highest, mathematical level we map maps on maps that map maps on maps and so forth. In the course of this book we will meet maps in different contexts.

Going back to the low-level considerations of mapping simple values like the character `'a'`, the number `97` and the instruction `POPA` onto clusters of bits (in this case bytes), both of this values are mapped to the same byte `01100001`, but  how does the computer know, how to distinguish them? One answer is that the computer does not really care and in most cases does not really have to care. I a character `'a'` is typed into a computer and internally stored as `01100001`, the computer can make calculations with it just as if it was the number `97`, and in many cases this is also what the user wants. For example to change the lower case `'a'` to upper case `'A'` the computer simply subtracts the binary value of `32` from `97` to get `65` which has the binary representation `01000001` which corresponds to `'A'`. Every character of the 26 Latin letters can be switched from lower to upper case by subtracting `32` and from upper to lower case by adding `32`. There are even programming languages where `'a' - 32` is a valid expression. But there are cases that require to distinguish between the different behind-the-curtain-meanings of the bits. One way to distinguish types of values is by adding some additional bits, just to identify the following value. Since that requires additional space for every value in memory, the basic low-level method works differently: different types of values are stored in different areas of the memory, therefore a values type is implicitly know. It is important to note, that the type information does not only contain information relevant for a human, like if it is a character, a integer, a floating point value, a Boolean value of `true` of `false`, but also, for computing even more important, the length of the value. E.g. there are 8-bit, 16-bit, 32-bit and other integer lengths. The computer can address every single byte in memory (8 bits at a time), a 8-bit integer therefore consists of 1 byte, a 16-bit integer of 2 bytes etc.

On a higher level, everything that can mathematically be mapped to a number can have a abstract representation in a computer as a binary number. For example a color can be represented by three components red, green and blue as a numerical value representing the intensity for that color. An entire computer screen can be represented by millions of colors, three values for each pixel. 60 screens per seconds can represent the content on a screen over time, a video for example. All of this is just a very long binary number color after color, pixel by pixel, screen by screen in memory. Another, trivial example is a mapping of arbitrary abstract objects to integers; this can basically be anything we want to keep track of. For example

```
boat  > 0
house > 1
chair > 2
```

It makes no sense to use this number representations of this irl things to calculate something, the numbers are just a representation of the thing, nothing more. But they could be used to store store the result of a selection of these three options as a short number. This kind of mapping is also called a *enumeration* or short *enum*. Instead of just enumerating irl things, it is also possible to map more complex data structures to things, an example for that was the mapping of a color to its three intensities for red, green and blue. In the example of `boat`, `house` and `chair` it could be a value for weight and price:

```
boat  > {weight: 200, price: 50}
house > {weight: 1000, price: 150}
chair > {weight: 5, price: 2}
```

In this case it makes sense to use the values for calculations, for example to calculate the price of 3 `boat`s, to sum up the weight for a boat and a chair or to calculate the price per weight for each. As a side note, in this example it is not stated which unit or currency is attached to those values, so we have to make a mental map for each value and keep the units in mind. But it is also possible to keep units in the data structure; since a unit is only applicable to one value, we would have to put another data structure into our data structure. And yes, it is possible to nest data structures to virtually any required degree. 

```
boat > {
	weight: {value: 200, unit: kg},
	price:  {value: 50, currency: Dollar}
}
house > {
	weight: {value: 1000, unit: kg},
	price:  {value: 150, currency: Schilling}
}
chair > {
	weight: {value: 5, unit: kg},
	price:  {value: 2, currency: Dollar}
}
```

In this case we can utilize a enum for the units and currencies, since they are showing up multiple times.

```
kg > 0
Dollar > 1
Schilling > 2
boat > {
	weight: {value: 200, unit: 0},
	price:  {value: 50, currency: 1}
}
house > {
	weight: {value: 1000, unit: 0},
	price:  {value: 150, currency: 2}
}
chair > {
	weight: {value: 5, unit: 0},
	price:  {value: 2, currency: 1}
}
```

