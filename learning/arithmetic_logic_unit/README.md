# Arithmetic Logic Unit (ALU)

**We want our CPU to do more operations than just addition and subtraction.**

- From Assembly knowledge, we know that there is a bijection between CPU
instructions and opcodes (simple machine code binary). We will design the CPU
so that it can handle 4-bit opcodes, since 16 possible operations is a pretty
good number for this computer.

*The following ALU and instruction architecture does NOT belong to me!*

```text
           Opcode
          (4 bits)
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
```

*The text scheme from above was generated with the help of Claude Opus 4.8.*

- Much respect and appreciation to
[Polymath Unlimited](https://www.youtube.com/@PolymathUnlimited-du2hg)
for sharing amazing ideas to construct this masterpiece!

- The video that helped for desigining the ALU:
[How A Computer Thinks: Designing an ALU From Scratch (The CPU You Can Build, Ep. 6)](https://www.youtube.com/watch?v=yJoQj21jX_c)

- I did some little modifications so that the instructions used in the video
map into real Intel x86 mnemonics. See the video and compare if interested.

**Opcodes:**

```text
- 0000 (0x0): ADD - Basic addition, A + B
- 0001 (0x1): ADC - Addition with carry bit if last op. generated a carry
- 0010 (0x2): SUB - Basic subtraction, A - B
- 0011 (0x3): SBB - Subtraction with borrow if last op. did not generate carry
- 0100 (0x4): NOT - One's complement, bitwise invert B
- 0101 (0x5): NEG - Two's complement, integer opposite B
- 0110 (0x6): AND - Basic bitwise AND
- 0111 (0x7): OR  - Basic bitwise OR
- 1000 (0x8): XOR - Basic bitwise XOR
- 1001 (0x9): SHL - Logical left shift on B
- 1010 (0xa): SHR - Logical right shift on B
- 1011 (0xb): SAR - Arithmetic right shift on B
- 1100 (0xc): ROL - Rotate left on B
- 1101 (0xd): ROR - Rotate right on B
- 1110 (0xe): RCL - Rotate left on B through carry
- 1111 (0xf): RCR - Rotate right on B through carry
```

