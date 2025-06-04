# Turbo Macro Pro: an assembly language development environment for C64

**Turbo Macro Pro (TMP)**, when loaded from a floppy disk with a command such as:

```BASIC
LOAD "TMP",8,1
```

or equivalent, depending on your drive and disk setup, can usually be executed (started) with the BASIC command:

```BASIC
SYS 32768
```

as ``32768`` is the decimal translation of the hexadecimal ``$0800``, which is where the code is designed to be loaded into memory.

The ``,1`` parameter on the end of the BASIC command 

```BASIC
LOAD "TMP",8,1
```

means load into the preferred memory location specified in machine language code itself, rather than the next location available to BASIC or some other default fallback position.

This is why programmers working in machine code or assembly language usually start by specifying an address where the program prefers to be loaded.
