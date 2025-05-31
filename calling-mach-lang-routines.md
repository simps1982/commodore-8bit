# Calling Machine Language Sub-Routines

## From within Assembly Language
``JSR [memory address of sub-routine]`` ("Jump to sub-routine") assembly language equivalent to ``GOSUB`` in BASIC.

``RTS`` ("Return from sub-routine") assembly language equivalent to ``RETURN`` in BASIC.

## From within BASIC
``SYS [decimal memory address of sub-routine]`` ("System") - e.g. ``SYS 8``.

## Notable built-in Machine Language Sub-Routines
The first three built-in routines programmers tend to memorise and use frquently are:
 * ``CHROUT`` (output an ASCII character)
 *  ``GETIN`` (catch an ASCII character from an input device)
 *  ``STOP`` (check the status of the STOP/RUN key on Commodore keyboard)

Sub-routines need to be called by means of the address at which they reside. Fortunately, the locations of these most frequently used routines are consistent across all the 8-bit Commodore machines.

* ``CHROUT`` lives at $FFD2
* ``GETIN`` lives at $FFE4
* ``STOP`` lives at $FFE1
