# Carry Lookahead Adder

**All the important details needed can be found in the following two videos:**

- [Carry Lookahead Adder (Part 1) | CLA Generator](https://www.youtube.com/watch?v=6Z1WikEWxH0)

- [Carry Lookahead Adder (Part 2) | CLA Adder](https://www.youtube.com/watch?v=9lyqSVKbyz8)

- Thank you, [Neso Academy](https://www.youtube.com/channel/UCQYMhOMi_Cdj1CEAU-fv80A)!

- The main idea is to save time (thinking about the real computer now) by not
waiting for each carry bit to ripple through the remaining adders so that the
current addder calculation can be done independently.

- Starting from the simple full adder boolean equation adapted to our 8-bit
full adder, we find a linear recursion with changing coefficients. There are
mathematical tools to find the explicit formula for each carry bit, but
induction works as well. I am not gonna derive anything here, since much
of it can be found in the videos above. The only rigour in those derivations
are related to the beautiful properites of boolean algbera... Proven them a
long time ago... Memories... .

- After completing one carry lookahead adder, we can then construct a 4-bit
lookahead adder using the found equations.

