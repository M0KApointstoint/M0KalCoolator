# Seven Segment Display

Youtube links that are helpful from
[Neso Academy](https://www.youtube.com/channel/UCQYMhOMi_Cdj1CEAU-fv80A):

- [Seven Segment Display Decoder](https://www.youtube.com/watch?v=smeUN1Bxj3M&t=2s)

- [Seven Segment Display Decoder (Part 2)](https://www.youtube.com/watch?v=_qGFpgpqf7s&t=25s)

- [Seven Segment Display Decoder (Part 3)](https://www.youtube.com/watch?v=vZKRs_1jPeI)

**Important:**
There are some mistakes that I found when computing *b* and *c* functions via
Karnaugh minimizations. You can look in the comments section as well for more
details.

**Boolean functions:**

```text
a = b3 + b1 + (!b2 * !b0) + (b2 * b0)

b = !b2 + (!b1 * !b0) + (b1 * b0)

c = b2 + !b1 + b0

d = b3 + (!b2 * !b0) + (!b2 * b1) + (b1 * !b0) + (b2 * !b1 * b0)

e = (!b2 * !b0) + (b1 * !b0)

f = b3 + (b2 * !b0) + (!b1 * !b0) + (!b1 * b2)

g = b3 + (b1 * !b0) + (b1 XOR b2)
```

