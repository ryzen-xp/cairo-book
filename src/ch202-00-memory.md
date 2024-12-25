# Memory

Most computers use memory that allows random access for reading and writing. This means a program can pick any memory location to either read its value or replace it with a new one. However, this isn't the only way memory can work. In purely functional programming, once a variable gets a value, it can't be changed. For such languages, a "write-once" memory model could work well and still run programs efficiently.

#### Here are three memory models considered for the Cairo architecture:
#### 1. Read-Write Memory:
The standard memory model where values can be read or overwritten.
```bash
write (
address=20, value=7)
...
x = read ( address=20)
```
#### 2. Write-Once Memory:
In this memory model, if you try to write to a memory cell that was already assigned a value, the write operation will fail.
Similarly, if you try to read before writing, the operation will fail.
```bash
write (
address=20, value=7)
...
x = read ( address=20)
```
#### 3. Nondeterministic Read-Only Memory:
In this memory model, the prover chooses all the values of the memory, and the memory is immutable.
The Cairo program may only read from it.
```bash
y = read ( address=20)
assert y == 7
...
x = read ( address=20)
```

