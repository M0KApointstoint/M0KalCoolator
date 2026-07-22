# 8-Bit Carry Lookahead Adder

- Since we are working with a small number of bits, instead of
chaining more and more gates to 4-bit CLA, we can combine two of
them to get one 8-bit CLA, still being fast relative to the
8-bit normal adder with ripple carry.

**Important:**

- Chaining requires too many gates. Also, the way that I combined
the two 4-bit CLA modules is still not very efficient, it can be done
in a much better way.

