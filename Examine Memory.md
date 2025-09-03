- *Concept*: Learn to use the `x `(examine) command to peek into memory (stack, instructions, etc.).
- *Why it matters*: Most vulnerabilities involve memory corruption (stack, heap). Being able to read memory helps you find where values are stored (e.g., random numbers, buffers, return addresses).

### Key Commands:

- `x/8i $rip` → disassemble 8 instructions from the instruction pointer.

- `x/16gx $rsp` → print 16 quadwords from the stack.

- `disassemble main` → show main’s instructions.

- `set disassembly-flavor intel` → switch to Intel syntax (easier for most exploit developers).
