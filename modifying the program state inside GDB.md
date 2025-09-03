### Key idea:
- With the `set` command, GDB can directly modify registers or memory while the program is running.
**Examples:**
 - Modify a register value:
```bash
set $rdi = 0
```
- Modify the top of the stack:
```bash
set *((uint64_t *) $rsp) = 0x1234
```
- Modify arbitrary memory at an address:
```bash
set *((uint16_t *) 0x31337000) = 0x1337
```
