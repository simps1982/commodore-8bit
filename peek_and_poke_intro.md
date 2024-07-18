# Introducing PEEK and POKE
Few will ever have spent much time using an 8-bit Commodore, such as the C-64, without having encountered the **PEEK** and **POKE** commands. I say commands, though technically POKE is an operating system command while PEEK is a **function** designed to return an integer when called.

PEEK and POKE respectively reveal the value stored at a specified memory address, and inject a value into a specified memory address. In other words, they are extremely powerful, giving the user direct unfettered access to the real workings of their 8-bit microcomputer. Accordingly, while many problems may be solved, and solutions achieved, most efficiently through correct use of PEEK and POKE, such fundamental commands do have the potential to compeletely freeze the computer, requiring a hard reboot, or to overwrite one's current program, erasing it from memory.

## Syntax of PEEK and POKE
PEEK and POKE commands take the following form:
- **PEEK (ADDRESS)**
- **POKE ADDRESS, VALUE**

where ADDRESS and (where applicable) VALUE are both integers (whole numbers).

The parentheses (rounded brackets) are vital when using PEEK, as it is a function.

## Learning the POKE command
Probably the most common way for new users to begin to build familiarity with POKE on their Commodore is to simply change the colour of the fundamental elements of their display:
 - border colour;
 - background colour;
 - text color.

These properties are usually set to an integer value in the range 0-16.

Each is stored at a memory address as follows:
 - border colour: 53280
 - background colour: 53281
 - text colour: 646

### A beginner's example for POKE
- POKE 53280, 14
- POKE 53281, 0
- POKE 646, 1

The above sequence of POKE commands will give a pale blue border, a black screen background and white text: perhaps an easier-to-read combination than the C-64's famous default colour scheme.

### Using variables with POKE
The two parameters for a POKE command, **ADDRESS** and **VALUE** can be entered directly as numbers, as in the above example, but there are countless use cases in which it would be greatly advantageous to store them in a variable, and have the POKE command draw upon them from there. For brevity one might choose to call such a pair of variabes **A** and **B** in BASIC.

For example, to set the background colour to black (0):
- A = 53281
- V = 0
- POKE A, V
