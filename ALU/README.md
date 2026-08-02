# Arithmetic Logic Unit (ALU)

**I really recommend you first check the ALU `learning` bit:**

```bash
$ cd ../learning/arithmetic_logic_unit/
$ ls -l
```

**Abstract ALU scheme:**

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

**ALU Opcodes:**

```text
- 000 (0x0): ADD - Basic addition, A + B
- 001 (0x1): SUB - Basic subtraction, A - B
- 010 (0x2): AND - BASIC bitwise AND, A & B
- 011 (0x3): OR  - Basic bitwise OR, A | B
- 100 (0x4): XOR - Basic bitwise XOR, A ^ B
- 101 (0x5): NOT - One's complement, bitwise invert B, ~B
- 110 (0x6): SHL - Logical left shift on B, B << 1
- 111 (0x7): SHR - Logical right shift on B, B >> 1
```

**ALU Flags:**

```text
- Carry flag   : (CF) - The result generated a carry
- Zero flag    : (ZF) - The result is zero
- Negative flag: (SF) - The result is negative (with sign bit on)
- Overflow flag: (OF) - The result generated an overflow
```

**Detailed ALU scheme:**

```text
                       Opcode
A ───┐                   │
     ▼                   ▼
  ┌─────┐            ┌───────┐
  │ ADD │─── 000 ───▶│       │
  ├─────┤            │       │
  │ SUB │─── 001 ───▶│       │
  ├─────┤            │       │
  │ AND │─── 010 ───▶│       │
  ├─────┤            │       │
  │ OR  │─── 011 ───▶│ 8 : 1 │
  ├─────┤            │  MUX  │───▶ Result
  │ XOR │─── 100 ───▶│       │       │
  ├─────┤            │       │       ▼
  │ NOT │─── 101 ───▶│       │┌─────────────┐
  ├─────┤            │       ││    Flags    │
  │ SHL │─── 110 ───▶│       ││   CF · ZF   │
  ├─────┤            │       ││   SF · OF   │
  │ SHR │─── 111 ───▶│       │└─────────────┘
  └─────┘            └───────┘
     ▲
B ───┘
```

Some of the operations from above can be implemented using parts of our full
adder that can also do subtraction, I recommend you check out the circuit:

```bash
$ cd ../learning/adders/8bit_adder_with_subtraction/
$ ls -l
```

- The `ADD` and `SUB` operations are already implemented

- The `AND` operation can be implemented using adder internals when `subtract`
is set to zero

- The `OR` operation can be implemented using actual OR gates

- The `XOR` operation can be implemented using adder internals when `subtract`
is set to zero

- The `NOT` operation can be implemented using adder internals when `subtract`
is set to one

- The `SHL` operation can be implemented using: TODO

- The `SHR` operation can be implemented using: TODO

