# 1-bit ALU

- Thanks to [Ryan Meuth](https://www.youtube.com/@RyanMeuth/videos) for
the design ideas!

- Video of inspiration:
[CSE 230 - LogiSim ALU Tutorial](https://www.youtube.com/watch?v=dYZ-Hwbcnq4)

- I did some modifications but the core idea comes from above.

**Opcodes (8-bit):**

```text
000: NOT (A)
001: AND
010: OR
011: XOR
100: NAND
101: NOR
110: ADD
111: SUB (A - B)
```

