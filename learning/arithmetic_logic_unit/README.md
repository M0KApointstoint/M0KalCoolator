# Arithmetic Logic Unit (ALU)

- This **amazing** video from
[Core Dumped](https://www.youtube.com/@CoreDumpped) is very useful for
understanding the basics of ALUs, starting from the transistor level, which
maps perfectly to the real life objective of this project, I really recommend
you watch it:
[HOW TRANSISTORS RUN CODE?](https://www.youtube.com/watch?v=HjneAhCy2N4)

**We want our CPU to do more operations than just addition and subtraction.**

- From Assembly knowledge, we know that there is a bijection between CPU
instructions and opcodes (simple machine code binary). We will design the CPU
so that it can handle 3-bit opcodes, since 8 possible operations is a pretty
good number for this computer.

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

- Some videos from
[Polymath Unlimited](https://www.youtube.com/@PolymathUnlimited-du2hg)
that helped for desigining the ALU:
- [How A Computer Thinks: Designing an ALU From Scratch (The CPU You Can Build, Ep. 6)](https://www.youtube.com/watch?v=yJoQj21jX_c)

- [Finishing the ALU (The CPU You can Build, ep. 7)](https://www.youtube.com/watch?v=O43Qrq3CDs4&t=108s)

- There are some differences between the instruction codes used in the video
and the instruction codes used by me. We sit somewhere between `Ben Eater`
and `Polymath Unlimited`.

- I named the instructions so that they can map into real Intel x86 mnemonics.
See the videos and compare if interested.

**ALU Opcodes:**

```text
- 000 (0x0): ADD - Basic addition, A + B
- 001 (0x1): SUB - Basic subtraction, A - B
- 010 (0x2): AND - BASIC bitwise AND, A & B
- 011 (0x3): OR  - Basic bitwise OR, A | B
- 100 (0x4): XOR - Basic bitwise XOR, A ^ B
- 101 (0x5): NOT - One's complement, bitwise invert A, ~A
- 110 (0x6): SHL - Logical left shift on A, A << 1
- 111 (0x7): SHR - Logical right shift on A, A >> 1
```

*Choosing the ALU opcodes was done with the help of Claude Opus 4.8.*

**Flags:**

```text
- Carry flag   : (CF) - The result generated a carry
- Zero flag    : (ZF) - The result is zero
- Negative flag: (SF) - The result is negative (with sign bit on)
- Overflow flag: (OF) - The result generated an overflow
```

