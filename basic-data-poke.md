# Using BASIC to combine POKE statements with DATA statements

In many variants of **BASIC**, including Commodore's, the `DATA` keyword can be a useful alternative to arrays for feeding batches of data into a program *en masse* to populate one or many variables.
The BASIC command `READ` reads one line of data at a time into the specified BASIC variable or variables.

On 8-bit Commodore microcomputers, especially in the early years, prior to the wide availability of assembler software packages, one popular way to enter **raw machine code** programs was to assign every byte of the program and its associated data to a series of `DATA` statements in BASIC, and then write a simple **loader** consisting of a few lines of BASIC, often with a simple loop structure, to read the data, store it at an appropriate addresss space where it will not conflict with the operating system kernel (or "Kernal" in Commodore's unconventional spelling) or with the BASIC interpreter, and then execute it using the `SYS` statement specifying the program's start address.

A relatively easy way to learn the fundamentals of this **"loader"** technique long before one has learned machine language, binary notation or the like, is to use a combination of `POKE` and `DATA` in a short BASIC program to efficiently set several user interface parameters, such as display colours. In such a small example as this, there is no need for a `SYS` statement, as `POKE` will suffice.

## First example: set blue border, black background and white text
``` BASIC
10 PRINT CHR$(147)
20 READ A, V
30 IF A = 0 AND V = 99 THEN END
40 POKE A, V
50 GOTO 20
100 DATA 53280,6
110 DATA 53281,0
120 DATA 646,1
130 DATA 0,99
```

### Double-check your code, fix if necessary
``` BASIC
LIST
```

Will print to screen all the BASIC code currently in memory. If you see a mistake on a line, simply replace it with a corrected version by typing a new line beginning with the same line number as the problematic line e.g 50. Next time you enter `LIST` you will see the amended version has replaced the old in memory.

To view a particular line of code, simply enter the `LIST` command and the line number e.g.:
``` BASIC
LIST 50
```

If you realise you forgot to enter a particular line, or need to **insert a new line** somewhere amongst the others, just pick an intermediate line number e.g. 35 if you need to insert a line in between lines 30 and 40.

To **erase a line** completely simply enter the line number and hit ENTER. The next execution of the `LIST` command will show that the unwanted line has disappeared from memory.

BASIC line numbers are arbitrary, but it is customary to use the ten times table for this reason: it leaves you scope to swiftly insert additional lines at any point later and facilitates easy correction of mistakes.

There are various other loose-knit conventions for line numbering: some programmers like to start their 'DATA' statements with a round key number like 100, 1 000 or 10 000 even if the previous line number was only 50 or 60 and then resume counting in tens henceforth.

It is a general custom for beginners to list `DATA` statements together at either the start or the end of a program unless you have a specific reason not to. In this example snippet the placement will make no noticeable difference, but in a much longer program with heavy use of `GOTO` or `GOSUB` and `RETURN`, there could be a significant performance overhead to placing `DATA` statements elsewhere.

### Test run your code
``` BASIC
RUN
```

If the execution produces an error message, `LIST` your code again, try a change, and repeat until it works as intended.

### Explanation
This code snippet is comprised primarly of address-value pairs, saying "please inject this value into this memory address." 
 - Border (address 53280) is set to blue (6)
 - Background (address 53281) is  set to black (0)
 - Text (address 646) is set to white (1)

When A, as read from a `DATA` line, equals 0 (tested on line 30) the program exits with the `END` command, thereby breaking out of the potentially infinite loop setup by the `GOTO` instruction. The program will `READ`-then-`POKE` in a loop until double-zero data line is encountered.

The first line (10), which prints to screen character 147, a special **control character,** is early versions of Commodore BASIC's way of **clearing the screen** in the absence of a dedicated clear screen command such as `CLS` found in many other BASIC dialects. `CHR$()` is a builtin function which takes an integer argument and returns a character.

This sort of **loop-until-end-of-data-detected** mechanism can be useful in situations where one wishes to keep changing the amount of data without undue constraint. The values chosen to represent the end of the dataset are arbitrary: while (0, 99) was chosen for this simple example and worked well, this would obviously not be an acceptable choice in a project handling statistical data in which some of the real entries could conceivably equal 0 or 99, e.g. *points scored* or *number of ducks spotted on the lake today*.

(0, 99) made sense as the end-of-data marker in this snippet, as we are reading (memory address, colour value) pairs, and 0 does not make sense as an address we would wish to write a colour to, and 99 is easy to remember and well outside the range (0-15) of Commodore colours for this situation.

In this short example program all `DATA` statements contained only pairs of integers, but some programs will use `READ` and `DATA` to read BASIC's other data types into variables of the matching types e.g. V$ could be the variable name for storing **string** values.
