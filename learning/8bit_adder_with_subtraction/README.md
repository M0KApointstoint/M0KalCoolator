# 8-Bit Adder
## With Subtraction

- From a more mathematical point of view, subtraction is really addition
with a minus sign and since we are working with integers (ring properties
blah blah blah...) we can use two's complement to complete our 8-bit adder.

- For now we can perform simple unsigned addition with 8-bit integers like
this:

```text
A + B
```

- In order to perform subtraction we do:

```text
A - B = A + (-B)
```

- Using two's complement, in order to calculate the opposite of B, we first
flip it's bits and add one at the end. This can be implemented in our simple
8-bit adder using XOR gates the first carry-in bit, and another input pin that
triggers subtraction.

- Also, when it comes to subtraction, the last "carry" can show us if B is
 greater than A or not, because since we are working with one byte, negating B
is equivalent to calculating 255 - B, therefore we have that:

```text
A - B = A + (-B) = A + (255 - B) + 1 = (A - B) + 256
```

- That 256 at the end is our nine bit 100000000 which makes the "carry" bit go
on.

