# Arithmetic Logic Unit (ALU)

This **amazing** video from
[Core Dumped](https://www.youtube.com/@CoreDumpped) is very useful for
understanding the basics of ALUs, starting from the transistor level, which
maps perfectly to the real life objective of this project, I really recommend
you watch it:
[HOW TRANSISTORS RUN CODE?](https://www.youtube.com/watch?v=HjneAhCy2N4)

**We want our CPU to do more operations than just addition and subtraction.**

From Assembly knowledge, we know that there is a bijection between CPU
instructions and opcodes (simple machine code binary). We will design the CPU
so that it can handle 3-bit opcodes, since 8 possible operations is a pretty
good number for this computer.

**Abstract ALU view:**

```text
         ALU Opcode
          (3 bits)
             │
             ▼
          ┌─────┐
   A ───▶ │     │
(8 bits)  │     │
          │ ALU │ ───▶ Result
   B ───▶ │     │     (8 bits)
(8 bits)  │     │
          └─────┘
             │
             ▼
           Flags
         (4 flags)
```

*The text scheme from above was generated with the help of Claude Opus 4.8.*

Some videos from
[Polymath Unlimited](https://www.youtube.com/@PolymathUnlimited-du2hg)
that helped for desigining the ALU:
- [How A Computer Thinks: Designing an ALU From Scratch (The CPU You Can Build, Ep. 6)](https://www.youtube.com/watch?v=yJoQj21jX_c)

- [Finishing the ALU (The CPU You can Build, ep. 7)](https://www.youtube.com/watch?v=O43Qrq3CDs4&t=108s)

**Important note:**

There are **many** differences between the design chosen by me and
`Ben Eater's` and `Polymath Unlimited's` designs. I like to say that we are
somewhere near the middle.

**The main objective is learning as much as possible but being *unique* too!**

I **really** recommend you watch `Ben Eater's` videos on the ALU topic as well:

- [ALU Design](https://www.youtube.com/watch?v=mOVOS9AjgFs)

- [Building the ALU](https://www.youtube.com/watch?v=S-3fXU3FZQc)

*The two videos from below are related to debugging but still useful to watch:*

- [Troubleshooting the ALU](https://www.youtube.com/watch?v=U7Q8-2YZTUU)

- [Testing the computer's ALU](https://www.youtube.com/watch?v=4nCMDvnR2Fg)

I named the instructions so that they can map into real Intel x86 mnemonics.
See the videos and compare if interested.

**ALU Operations:**

```text
- ADD : Basic addition, A + B
- SUB : Basic subtraction, A - B
- AND : Bitwise AND, A & B
- OR  : Bitwise OR, A | B
- XOR : Bitwise XOR, A ^ B
- NOT : One's complement, bitwise invert B, ~B
- SHL : Logical left shift on B, B << 1
- SHR : Logical right shift on B, B >> 1
```

Starting from the 8-bit adder circuit that can also do subtraction we can
take into account already used internal logic to get other operations as well:

- The `ADD` and `SUB` operations are already implemented using the `subtract`
bit set to zero and one, respectively

- The `AND` operation can be implemented using adder internals when `subtract`
is set to zero

- The `OR` operation can be implemented using actual OR gates

- The `XOR` operation can be implemented using adder internals when `subtract`
is set to zero

- The `NOT` operation can be implemented using adder internals when `subtract`
is set to one

- The `SHL` and `SHR` operations can be implemented only using the input wires,
very easy to do

**ALU Opcodes:**

Since opcodes represent inputs for the 8 : 1 multiplexers that select each bit
from the result, we need to choose operation codes that will save hardware
materials and keep the circuit nice:

```text
| Operation | Subtract bit |
|-----------|--------------|
|    ADD    |      0       |
|    SUB    |      1       |
|    AND    |      0       |
|    OR     |      *       |
|    XOR    |      0       |
|    NOT    |      1       |
|    SHL    |      *       |
|    SHR    |      *       |
```

Since every operation has a 3-bit opcode we need to make some sort of
`reverse engineering` on `Karnaugh map` minimization.

The following mapping seems the most appropiate to my taste:

```text
| Operation | Code |
|-----------|------|
|    ADD    | 000  |
|    AND    | 001  |
|    SUB    | 010  |
|    NOT    | 011  |
|    XOR    | 100  |
|    OR     | 101  |
|    SHL    | 110  |
|    SHR    | 111  |
```

```text
|  O2 \ O1O0  |  00  |  01  |  11  |  10  |
|-------------|------|------|------|------|
|      0      |  0   |  1   |  *   |  0   |
|      1      |  0   |  1   |  *   |  *   |
```

**Abstract view of an 1-bit ALU chunk from the 8-bit ALU:**

```text
                  Opcode
A0 ───┐           │ │ │
      ▼           ▼ ▼ ▼
   ┌──────┐    ┌───────────┐
   │ ADD0 │───▶│000        │
   ├──────┤    │           │
   │ AND0 │───▶│001        │
   ├──────┤    │           │
   │ SUB0 │───▶│010        │
   ├──────┤    │           │
   │ NOT0 │───▶│011  8 : 1 │
   ├──────┤    │      MUX  │───▶ Result0
   │ XOR0 │───▶│100        │
   ├──────┤    │           │
   │ OR0  │───▶│101        │
   ├──────┤    │           │
   │ SHL0 │───▶│110        │
   ├──────┤    │           │
   │ SHR0 │───▶│111        │
   └──────┘    └───────────┘
      ▲
B0 ───┘
```

**Flags:**

```text
- Carry flag   : (CF) - The result generated a carry
- Zero flag    : (ZF) - The result is zero
- Negative flag: (SF) - The result is negative (with sign bit on)
- Overflow flag: (OF) - The result generated an overflow
```

