# Logic
The word 'logic' is derived from the Greek word λόγος (logos) which means among other things 'word', 'speech', 'reason'. It made its way from Plato's Theory of Ideas into the Bible, famously at the beginning of the Gospel of John:

>In the beginning was the Word, and the Word was with God, and the Word was God.

>Ἐν ἀρχῇ ἦν ὁ λόγος, καὶ ὁ λόγος ἦν πρὸς τὸν θεόν, καὶ θεὸς ἦν ὁ λόγος.

It is also used as the suffix '-logy' for bodies of knowledge, like in 'psychology' or 'topology'. For common speech it is also used as a indicator for reasoning. But for programming we require a more precise understanding of logic we want to utilize. The two types of logic we are going to use are *predicate logic* and its little sister *propositional logic*. 

## Propositional Logic
Propositional logic uses the simple logical operators `and`, `or` and `not`(upon others) to express a logical statement from other logical statements:

>Scrooge McDuck is rich `and` Donald Duck is rich

is a false (propositional) logical statement, since Scrooge is actually rich, but Donald is notoriously poor, and if one statement in a `and` statement is false, the entire `and`-statement is false. But the statement

>Scrooge McDuck is rich `and` (Donald Duck is `not` rich)

is true since the second statement is now negated, which makes it true. When we use variables for statements, the it is not clear anymore if the statements are true or not.
```
A and not B
```
But we are now able to make statements depending on their Boolean value. If `A` is `true` and if `B` is false, the entire statement is `true`. If `A` is `false` or `B` is `true` the entire statement will be `false`; this is also the case if `A` is `flase` and `B` is true at the same time. Therefore we have all four cases covered:
```
| A     | B     | A and not B |
|-------+-------+-------------|
| true  | true  | false       |
| true  | false | true        |
| false | true  | false       |
| false | false | false       |
```

## Predicate Logic
The basic statements in propositional logic can either be true or false, depending on their predefined condition, or more precisely, depending on the value they were assigned to. With predicate logic it is also possible to express logic statements depending on numbers. For example
```
x < 3
```
If this statement is true or false depends on `x`. Such statements can also be combined with Boolean operators:
```
x < 3 or x > 5
```
In this case the entire statement is true if `x` is smaller than 3 and it is true if `x` is larger than 5.