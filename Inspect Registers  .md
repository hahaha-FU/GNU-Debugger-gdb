- *Concept*: Learn how to view and print register values.

- *Why it matters*: Registers store critical data like function arguments, return addresses, and random values. You must know how to read them for reverse engineering or buffer overflow exploits.

### Key Commands:

- `info registers` → shows all registers.
- `p $r12` → prints r12 in decimal.
- `p/x $r12` → prints r12 in hex.
