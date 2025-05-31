# Supermon+64: Jim Butterfield's famous Machine Language Monitor (MLM) program

## Location
Many versions of **Supermon+64** conveniently display the memory address at which the program lives immediately after the title line upon being loaded and run from media such as floppy disk, and provide a reminder of how to safely re-enter the Monitor after an accidental exit back to the BASIC prompt, such as:

```BASIC
SYS 38169
```

## Memory bank areas
Generally $C000 - $CFFF is an address space range to use for one's own small machine language programs when coding with **Supermon+64.**

Note that this same range is NOT available when using some assembler packages, such as **Turbo Macro Pro** (the famous **TMP**) which occupy some or all of this range for their internals.
