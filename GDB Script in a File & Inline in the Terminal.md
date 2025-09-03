🔹 Method 1: GDB Script in a File
1. Create a file called collect.gdb:
```bash
nano collect.gdb
```
2. Put this inside:
```bash
start
break *main+42
commands
  silent
  set $val = *(unsigned long long*)($rbp-0x32)
  printf "Random value: %llx\n", $val
  continue
end
continue
```
3. Run it:
```bash
gdb -q -x collect.gdb /challenge/embryogdb_levelXYZ
```
______________________
🔹 Method 2: Inline in the Terminal
-Instead of a file, you can use `-ex` flags:
```bash
gdb -q \
  -ex "start" \
  -ex "break *main+42" \
  -ex "commands" \
  -ex "silent" \
  -ex "set \$val = *(unsigned long long*)($rbp-0x32)" \
  -ex "printf \"Random value: %llx\n\", \$val" \
  -ex "continue" \
  -ex "end" \
  -ex "continue" \
```
____________
### Line-by-Line Explanation
- `start`
→ Launch the program and stop at the beginning of `main`.
- `break *main+42`
→ Set a breakpoint at the instruction 42 bytes into main. (This is where the random value is accessed).
- `commands`
→ Start defining commands that will run automatically when this breakpoint is hit.
- `silent`
→ Suppress GDB’s default message (“Breakpoint hit at …”). Keeps output clean.
- `set $val = *(unsigned long long*)($rbp-0x32)`
→ Read the 8-byte value stored at `$rbp-0x32` (a local stack variable), and store it in a custom GDB variable `$val`.
- `printf "Random value: %llx\n", $val`
→ Print the variable in hex format with a label.
- `continue`
→ Resume program execution until the breakpoint is hit again.
- `end`
→ End the breakpoint command block.
- `continue`
→ After setting everything up, start the program so it can hit the breakpoint.
____

 *So the flow is:*

1. Start program →
2. Breakpoint at main+42 →
3. Every time it’s hit: silently grab stack value → store in $val → print nicely → continue →
4. Loop until program finishes
