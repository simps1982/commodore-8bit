# Supermon+64: Jim Butterfield's famous Machine Language Monitor (MLM) program

## Location
Many versions of **Supermon+64** conveniently display the memory address at which the program lives immediately after the title line upon being loaded and run from media such as floppy disk, and provide a reminder of how to safely re-enter the Monitor after an accidental exit back to the BASIC prompt, such as:

```BASIC
SYS 38169
```

## Memory bank areas
Generally $C000 (decimal 49152) - $CFFF (decimal 53247) is a popular address space range to use for one's own small machine language programs when programming the **C64** with **Supermon+64.**

For relatively trivial example programs of a few lines, one might begin entering code at $C000, and store any associated data, such as a "HELLO WORLD" string, at $C1000. Such a program could then by run by exiting to the BASIC prompt and entering

```BASIC
SYS 49152
```

as the ``SYS`` BASIC command expects a memory address expressed in decimal, not hexadecimal.

Note that this same memory range is NOT available when using some assembler packages, such as **Turbo Macro Pro** (the famous **TMP**) which occupy some or all of this range for their internals. Accordingly, a programmer should always determine the range of addresses which remain available when using software packages to aid or ease development.
