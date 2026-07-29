# Parity Light Control Circuit

**Task:**
- We need to build a simple logic circuit that turns an LED on if and only if
for a given natural number (n) of inputs, only an odd number of them are turned
on.

*Solution:*
- First, we are gonna consider the n = 2 case and build the truth table:
```text
| x | y |LED|
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |
```

- We find that this is the exact truth table for the XOR gate, therefore we
can write that:
```text
LED = x XOR y
```

- Inductively, using XOR associativity, we find that for n inputs,
a_1, a_2, ..., a_n, the LED equation is:
```text
LED = a_1 XOR a_2 XOR ... XOR a_n
```

*Made by M0KApointstoint*

