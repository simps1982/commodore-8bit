
# Introducing PEEK and POKE
Few will ever have spent much time using an 8-bit Commodore, such as the C64, without having encountered the `PEEK` and `POKE` commands. I say commands, though technically `POKE` is an operating system command while `PEEK` is a **function** designed to return an integer when called.

`PEEK` and `POKE` respectively reveal the value stored at a specified memory address, and inject a value into a specified memory address. In other words, they are extremely powerful, giving the user direct unfettered access to the real workings of their 8-bit microcomputer. Accordingly, while many problems may be solved, and solutions achieved, most efficiently through correct use of PEEK and POKE, using so powerful a command as POKE does have the potential to compeletely freeze the computer, requiring a hard reboot, or to overwrite one's current program, erasing it from memory.

Although a whole sub-culture, complete with tee-shirts and mugs, built on **PEEK-and-POKE-centered-programming** is perhaps most strongly associated with the C64, countless variants of BASIC running on a range of hardware platforms also use these two reserved keywords.

`POKE` was commonly used to gain an advantage in C64 games, usually by using a special accessory cartridge to freeze a game in play and hacking a copy of the code in RAM to provide unlimited retries or access to the final level or the full range of advanced weapons, for example, once the memory addresses of these variables had been discovered, whether by painstaking trial-and-error or by looking them up in magazines.

For a time, some gaming sub-culture vernaculars used 'Pokes' and 'Cheat codes' interchangeably. Some magazines published tables full of 'Pokes' (meaning cheat code mumbers).

## Syntax of PEEK and POKE
PEEK and POKE commands take the following form:
- `PEEK(ADDRESS)`
- `POKE ADDRESS, VALUE`

where ADDRESS and (where applicable) VALUE are both integers (whole numbers).

The parentheses (rounded brackets) are vital when using `PEEK`, as it is a function designed to return a single-byte integer value.

Perhaps the most common use of the `PEEK()` function among new users will be in conjunction with a `PRINT` statement, to display on screen a value captured from a specified memory location.
Another likely use case is to store the value returned by `PEEK(ADDRESS)` in a BASIC variable for use later in the program.

### A beginner's example to use PEEK() to capture the number of columns available to the display
```BASIC
C = PEEK(781)
PRINT "THIS DISPLAY HAS" C "COLUMNS."
```

On an unmodified C64 the expected result would be 40 columns.

## Learning the POKE command
Probably the most common way for new users to begin to build familiarity with POKE on their Commodore is to simply change the colour of three fundamental elements of their display:
1. border colour;
2. background colour;
3. text color.

These properties are usually set to an integer value in the range 0-15.

On a Commodore 64, each property is stored at the following memory addresses:
1. border colour: **53280**
2. background colour: **53281**
3. text colour: **646**

If you would like to use a different model microcomputer, you will need to consult the relevant manual to look up their equivalents.

### A beginner's example for POKE
``` BASIC
POKE 53280, 14
POKE 53281, 0
POKE 646, 1
```

The above sequence of POKE commands will give a pale blue border, a black screen background and white text: perhaps an easier-to-read combination than the C64's famous default colour scheme.

### Using variables with POKE
The two parameters for a POKE command, **ADDRESS** and **VALUE** can be entered directly as numbers, as in the above example, but there are countless use cases in which it would be greatly advantageous to store them in a variable, and have the POKE command draw upon them from there. For brevity one might choose to call such a pair of variabes **A** and **V** in BASIC.

For example, to set the background colour to black (0):
``` BASIC
A = 53281
V = 0
POKE A, V
```
