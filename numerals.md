# Numerals
At first it might not be obvious but the representation of a number and the number are not the same.  Numbers can have different representations and they all have to have the same meaning.  This static meaning is the foundation of the concept of separating representations from meaning; and it is also the basis for the platonic idea.
The Arabic and Roman representation for the number 4:
```
4 = IV
```
The Arabic representation uses ten different symbols for digits, therefore it has the base 10.  (It has ten digits because we have 10 digits.) 
```
0 1 2 3 4 5 6 7 8 9
```
If we have the representation of a number, how do we get its value?  For the same reason as above, this might not be clear at first.  We are not used to distinguish this things and might immediately thing: if we have hate digits, we have the number.  But this is not the case.  A simple example might clarify the problem:
After doing some OCR we might wind up having some digits in an array:
```
digits = [ 1, 3, 3, 7]
```
So how do we get the number 1337 out of it?  Again: it is not possible to say
```
number = digits[0]digits[1]digits[2]digits[3]
```
Because it is not the same to have some digits in succession and to have the number.
To get the number, we make use of what the digits mean: moving from right to left: 
* digit zero means 7 (its value), 
* digit two means 30 (its value times 10)
* digit three means 300 (its value times 100)
* digit four means 1000 (its value times 1000)
The worth of a digit depends on its value and on its position.

The result can be casted into a formula
```
number = digitsr[0]*10**0 + digitsr[1]*10**1
```

```
digits = [ 1, 3, 3, 7 ]
digits.reverse()
digits2number = (acc,el,i) => acc + el*10**i
digits.reduce(digits2number)
1337
```

```
digits2number = base => (acc,el,i) => acc + el*base**i
digits.reduce(digits2number(10))
1337
digits.reduce(digits2number(8))
735
```