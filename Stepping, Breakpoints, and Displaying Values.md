- *Concept*: Learn how to **control execution** (step, break, finish) and monitor values (with display).
- *Why it matters*: Sometimes you don’t want to just run until the program ends — you want to pause at the exact instruction that interests you, or watch how registers/memory change step by step. This is essential in exploit development when you trace how input flows into memory.

### Key Commands:

- `si / stepi` → step one instruction (enters functions).
- `ni / nexti` → step one instruction (skips over function calls).
- `break *<addr>` → set a breakpoint at an address.
- `finish` → run until current function returns.
- `display/4gx $rsp` → always show 4 stack values as execution continues.
- `layout regs` → TUI mode showing registers + code.
